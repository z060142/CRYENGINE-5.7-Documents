# Chapter 6 - Font Embedding

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/90833227
- Page ID: 90833227
- Breadcrumb: Tutorials > Game and Level Design > UI > UI Design Tutorials > Tutorial - Introduction to Scaleform UI > Chapter 6 - Font Embedding
- Parent: Tutorial - Introduction to Scaleform UI

## Content

##
What Do Font Glyphs Provide?

After you've set up all the fonts you wish to use in the UI, you should create localized copies of the font library for each language you wish to support.

The most optimized and efficient way to do this is to select a sub-set of glyphs that can be used in a particular language and only export this set of glyphs for that specific language. This saves disk and memory space, as only the necessary glyphs will be available.

##
Embedding Fonts

##
Scaleform 3

To embed fonts for dynamic text:

-
Navigate to the properties of your textbox and find the
**
Embed
**
**
...
**
 button to modify the font embedding options.

[Image: /docs/static/attachments/90833579]

*
Embed

*

-
Within these options, add the text "Score: 0123456789" to the
**
Also Include These Characters
**
: textbox.

[Image: /docs/static/attachments/90833230]

*
Also include these characters
*

-
Click
**
OK
**
in the Font Embedding window to finalize your changes and publish your project.

-
Following this, export your your SWF file to a GFx file as explained in
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456800](
Chapter 2 - Flash and Gfx
)
.

##
Scaleform 4

To embed fonts for dynamic text:

-
Navigate to the properties of your textbox and find the
**
Embed
**
**
...
**
 button to modify the font embedding options.

[Image: /docs/static/attachments/90833582]

*
Embed

*

-
Within these options, add the text "Score: 0123456789" to the
**
Also Include These Characters
**
: textbox.

[Image: /docs/static/attachments/90833232]

*
Also include these characters

*

-
Click
**
OK
**
in the Font Embedding window to finalize your changes and publish your project.

-
Following this, export your your SWF file to a GFx file as explained in
[/docs/static/engines/cryengine-5/categories/23756816/pages/89456800](
Chapter 2 - Flash and Gfx
)
.
[#what-do-font-glyphs-provide](
What Do Font Glyphs Provide?
)
[#embedding-fonts](
Embedding Fonts
)
[#scaleform-3](
Scaleform 3
)
[#scaleform-4](
Scaleform 4
)
