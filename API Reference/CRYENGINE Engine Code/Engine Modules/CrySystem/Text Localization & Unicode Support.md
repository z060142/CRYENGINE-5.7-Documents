# Text Localization & Unicode Support

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306431
- Page ID: 23306431
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CrySystem > Text Localization & Unicode Support
- Parent: CrySystem

## Content

#### Introduction

Since games are typically localized to various languages, there is a need to deal with potentially many languages while dealing with text data.

This document will provide some general information as well as CRYENGINE specific information aimed at programmers that will work with the source code. As such, for asset creation and design, please refer to [Localization](/docs/static/engines/cryengine-3/categories/1114113/pages/19377178) section for information on how to perform localization and create localized assets.

Starting with CRYENGINE version 3.8.1 we have done significant work in this area. This document applies to this version and newer versions.

#### Terminology

On this page, we will deal with some terminology and acronyms that are important to know about to understand this document. They are specific to the context of text processing. For more information on a specific term, consider using google or wikipedia entries.

Term | Description
--- | ---
character | A unit of textual data, can be a glyph or formatting indicator. Note that a glyph does not necessarily form a single visible "nit. Example, a diacretical mark ´ and a letter a are separate glyphs (and characters), but overlaid they form á
Unicode | A standard maintained by the Unicode Consortium that deals with text and language standardization
UCS | Universal Character Set, the standardized set of characters in the Unicode standard (also, ISO-10646)
(UCS) code-point | An integral identifier for a single character in the UCS defined range, typically displayed with the U prefix followed by hexadecimal: U+12AB
(text) encoding | (noun) A method of mapping (a subset of) UCS to a sequence of code-units (verb) The process of applying an encoding (the noun)
code-unit | An encoding-specific unit integral identifier used to encode code-points. Many code-units may be used to represent a single code-point.
ASCII | A standardized encoding that covers the first 128 code-points of the UCS space using 7- or 8-bit code-units
(ANSI) code-page | A standardized encoding that extends ASCII by assigning additional meaning to the higher 128 values when using 8-bit code-units There are many hundreds of code-pages, some of which use multi-byte sequences to encode code-points
UTF | UCS Transformation Format, a standardized encoding that covers the entire UCS space
UTF-8 | A specific instance of UTF, using 8-bit code-units. Each code-point can take 1 to 4 (inclusive) code-units
UTF-16 | A specific instance of UTF, using 16-bit code-units. Each code-point can take 1 or 2 code-units
UTF-32 | A specific instance of UTF, using 32-bit code-units. Each code-point is directly mapped to a single code-unit
byte-order | A way that a CPU treats a sequence of bytes when interpreting multi-byte values. Typically either little-endian or big-endian format
encoding error | A sequence of code-units that does not form a code-point (or an invalid code-point, as defined by the Unicode standard)

#### What encoding to use?

Since there are many methods of encoding text, the question that should be asked when dealing with even the smallest amount of text is, in what encoding is this stored? This is important, because decoding a sequence of code-units with a different encoding will lead to encoding errors (or worse, valid decoding yielding the wrong content)

An overview of some encodings and their properties:

encoding | code-unit size | code-point size | maps entire UCS space? | trivial to encode/decode? | immune to byte-order differences? | major users
--- | --- | --- | --- | --- | --- | ---
ASCII | 7 bits | 1 byte | no | yes | yes | Many english-only apps
(ANSI) code-page | 8 bits | varies, usually 1 byte | no | varies, usually yes | yes | Older OS functions
UTF-8 | 8 bits | 1 to 4 bytes | yes | no | yes | Most things on the internet, XML
UTF-16 | 16 bits | 2 to 4 bytes | yes | yes | no | Windows "wide" API, Qt
UCS-2 | 16 bits | 2 bytes | no | yes | no | None (replaced with UTF-16)
UTF-32 UCS-4 | 32 bits | 4 bytes | yes | yes | no | Linux "wide" API

As you can see, there is no single "best" encoding, so there is always the usage scenario to consider when picking an encoding.

Historically, this has lead to many operating systems and software packages to pick a (set of) supported encodings, but they seem to have picked different ones. Even different platforms in C++ have different conventions for their "wide character" wchar_t, for example, it is 16-bits on Windows but 32-bits on Linux.

Since CRYENGINE products can be used on many platforms and in many languages, we would like full UCS coverage. Here is the conventions that Crytek is moving towards with CRYENGINE:

text data type | encoding | reason
--- | --- | ---
source code | ASCII | We write our code in basic English, which means ASCII is sufficient.
text assets | UTF-8 | Assets can be transferred between machines with potentially differing byte-order, and may contain text in many languages.
run-time variables | UTF-8 | Since transforming text data from/to UTF-8 is not free, we keep the data in UTF-8 as much as possible. Exceptions must be made when interacting with libraries/OS that require another encoding, in which case all transformations should be done at the call-site.
file and path names | ASCII | File names are a special case with regards to equality, most commonly case-(in)sensitivity, as defined by the file system. Unicode defines 3 cases, and conversions between them are locale-specific. In addition, the normalization formats are typically not (all) accounted for in file-systems and their APIs. Note: Some specialized file-systems (some console cloud storage DBs) only accept ASCII. This combination means that using the most basic and portable sub-set should be preferred, fall back to UTF-8 only as required.

In general:

- Avoid using non-ASCII characters in source code, consider using escape sequences if an outside-ASCII literal is required
- Avoid using absolute paths so only paths under developer control need to be entered, use game-folder, root-folder or user-folder relative ASCII paths if possible. When this is impossible, carefully consider various non-ASCII contents that may be controlled by the user (such as installation folder)

#### How does this affect me when writing code?

Since the vast majority of text uses single-byte code-units, this means a single-byte string type can be used pretty much everywhere. In addition, since we do not deal with ANSI code-pages, we can be certain that all text is either ASCII or UTF-8.

The following properties hold for both ASCII and UTF-8

- The NULL-byte (integral value 0) only occurs when a NULL-byte is intended (UTF-8 never generates a NULL-byte as part of multi-byte sequences)
This means that null-terminated strings (C-style) act the same, and CRT functions like strlen will work as expected (except it counts code-units, not characters)
- Code-points in the ASCII range have the same encoded value in UTF-8
This means that you can type English string literals in code and treat them as UTF-8 without need for any conversion.
Also, you can compare characters in the ASCII range directly against UTF-8 content (ie, when looking for an English or ASCII symbol sub-string)
- UTF-8 sequences (containing zero or more entire code-points) do not carry context.
This means they are safe to append to each other without changing the contents of the text.

The different between position and length in code-units (as reported through string::length(), strlen() etc) and their matching position/length in code-points is largely irrelevant. This is because the meaning of the sequence is typically abstract, and only when the text is interpreted (ie, when displaying) does it matter what the bytes mean.

That said, there are some caveats:

- **String splitting**, when splitting a string, it's important to either:
- Recombine the parts in the same order after splitting, without interpreting the splitted parts as text (ie, chunking for transmission), or
- Perform the split at a boundary between code-points (Note: the positions just before and after any ASCII character are always safe)
- **API boundaries**, when an API accepts or returns strings:
Here it's important to know what encoding the API deals with. If the API doesn't treat strings as opaque (ie, interprets the text), passing UTF-8 may be problematic for APIs that accept byte-strings and interpret as ASCII or ANSI. If no UTF-8 API is available, prefer any other Unicode API instead (UTF-16 or UTF-32). As a last resort, convert to ASCII, but understand that the conversion is lossy and cannot be recovered from the converted string.
Always read the documentation of the API, to see what text encoding it expects, and perform conversion as required.
Note again: All UTF encodings can be losslessly converted between in both directions, so finding any API that accepts an UTF format gives you a way to use it.
- **Identifiers**, when using strings as a "key" in a collection or for comparison
Avoid using non-ASCII sequences as keys, as the concept of "equality" of UTF is complex due to normalization forms and locale-dependent rules
However, comparing UTF-8 strings byte-by-byte is safe if you only care about equality in terms of code-points (since code-point to code-unit mapping is 1:1)
- **Sorting,** when using strings for sorting
There are locale-specific rules for the order of text, that are complex. It's fine to let the UI deal with this in many cases. In general, make no assumptions on how a set of strings will be sorted.
However, sorting UTF-8 strings as if they were ASCII will actually sort them by code-point, which means that if you just need an arbitrary fixed order for std::map look-up it's fine, but displaying contents in the UI in this order may be confusing for end-users that expect another ordering.

In general, avoid interpreting text if at all possible. Otherwise, try to operate on the ASCII subset and treat all other text parts as opaque indivisible sequences. When dealing with the concept of "length" or "size", try to use the consider that in code-units instead of code-points, since those operations are cheaper. (In fact, the concept of "length" of Unicode sequences is complex, there is a many-to-many mapping between code-points and what is actually displayed)

#### How does this affect me when dealing with text assets?

In general, always:

- store text assets with the UTF-8 encoding.
- store with Unicode NFC (Normalization Form C), this is the "default" form in most text editing tools, and in the absence of other reasons it's best to standardize on the common.
- store text in the correct case (ie, the one that will be displayed), case-conversion is a complex topic in many languages, which is easiest to just avoid.

#### Utilities provided in CryCommon

Starting with CRYENGINE 3.8.1, we have added some utilities to make it easy to losslessly and safely convert text between Unicode encodings. In-depth technical details are provided in the header files that expose these utilities: `UnicodeFunctions.h` and ` UnicodeIterator.h`.

The most common use-cases:

`string utf8;` ` wstring wide;` ` Unicode::Convert(utf8, wide); // Convert contents of wide string and store into UTF-8 string` ` Unicode::Convert(wide, utf8); // Convert contents of UTF-8 string to wide string`

`string ascii;` ` Unicode::Convert<Unicode::eEncoding_ASCII, Unicode::eEncoding_UTF8>(ascii, utf8); // Convert UTF-8 to ASCII (lossy!)`

Note that all of the above functions assume that the input text is already validly encoded. To guard against user-input or potentially broken input, consider using the Unicode::ConvertSafe function instead.

#### Further reading

A good introduction can be found at [http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html).

See [http://unicode.org/](http://unicode.org/) for the official standard and more details on Unicode.
