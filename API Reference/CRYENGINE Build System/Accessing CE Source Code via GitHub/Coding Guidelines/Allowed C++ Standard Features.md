# Allowed C++ Standard Features

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/44972277
- Page ID: 44972277
- Breadcrumb: CRYENGINE Build System > Accessing CE Source Code via GitHub > Coding Guidelines > Allowed C++ Standard Features
- Parent: Coding Guidelines

## Content

A feature might be in either the '
Needs validation
',
'Allowed'
 or
'Disallowed'
 state. The significance of these states are as follows:

-
Needs validation

-
The feasibility of using the feature in CRYENGINE's code base is yet to be validated by the CRYENGINE's Technical Leads.

-
Allowed

-
The feature doesn't introduce 'show-blocking' issues.

-
The feature improves, or at least doesn't harm, code runtime and compile time performance.

-
The feature improves, or at least doesn't harm, code readability or debugability.

-
The feature is supported by all the compilers that the CRYENGINE code base is compiled against.

-
Disallowed

-
The feature introduces a 'show-blocking' issue.

-
The feature has a negative impact on runtime and compile time performance.

-
The feature has a negative impact on code readability and debugability.

-
The feature generally doesn't contribute to the overall quality and performance of the CRYENGINE code base.

-
The feature is not supported by a CRYENGINE code base compiler.

##
C++17 Language Features

**
Feature
**
 |
State
 |
Comments
 |

[Template argument deduction for class templates](https://github.com/AnthonyCalandra/modern-cpp-features#template-argument-deduction-for-class-templates)
 |
Needs validation
 |
-
 |

[Declaring non-type template parameters with auto](https://github.com/AnthonyCalandra/modern-cpp-features#declaring-non-type-template-parameters-with-auto)
 |
Needs validation
 |
-
 |

[Folding expressions](https://github.com/AnthonyCalandra/modern-cpp-features#folding-expressions)
 |
Needs validation
 |
-
 |

[New rules for auto deduction from braced-init-list](https://github.com/AnthonyCalandra/modern-cpp-features#new-rules-for-auto-deduction-from-braced-init-list)
 |
Needs validation
 |
-
 |

[Constexpr lambda](https://github.com/AnthonyCalandra/modern-cpp-features#constexpr-lambda)
 |
Needs validation
 |
-
 |

[Lambda capture this by value](https://github.com/AnthonyCalandra/modern-cpp-features#lambda-capture-this-by-value)
 |
Needs validation
 |
-
 |

[Inline variables](https://github.com/AnthonyCalandra/modern-cpp-features#inline-variables)
 |
Needs validation
 |
-
 |

[Nested namespaces](https://github.com/AnthonyCalandra/modern-cpp-features#nested-namespaces)
 |
Allowed
 |
This feature is considered light weight and doesn’t negatively impact code quality or run-time/compile-time performance. It is one of the first C++17 features adopted by compiler vendors, and has therefore been made available even on older tool-chains such as vc140. It is more of a cosmetic feature, since it helps improve readability in nested namespace scenarios.
 |

[Structured bindings](https://github.com/AnthonyCalandra/modern-cpp-features#structured-bindings)
 |
Needs validation
 |
-
 |

[Selection statements with initializer](https://github.com/AnthonyCalandra/modern-cpp-features#selection-statements-with-initializer)
 |
Needs validation
 |
-
 |

[Constexpr if](https://github.com/AnthonyCalandra/modern-cpp-features#constexpr-if)
 |
Needs validation
 |
The feature greatly simplifies compile-time branching that was only possible through overloading or specialization / SFINAE. It improves compile time and readability. The feature is available on all platforms and compilers (VS2017.3)
 |

[Utf-8 character literals](https://github.com/AnthonyCalandra/modern-cpp-features#utf-8-character-literals)
 |
Needs validation
 |
-
 |

[Direct-list-initialization of enums](https://github.com/AnthonyCalandra/modern-cpp-features#direct-list-initialization-of-enums)
 |
Needs validation
 |
-
 |

[New standard attributes [[fallthrough]], [[nodiscard]], [[maybe_unused]]](https://github.com/AnthonyCalandra/modern-cpp-features#new-standard-attributes)
 |
Allowed
 |
The [[nodiscard]] attribute, when put in front of function return type, can prevent discarding important return value or error code or misunderstanding the purpose of function. A typical example is the confusion of .empty() with .clear() in custom containers. With [[nodiscard]] the compiler issues a warning.
 |

[Terse static_assert](https://docs.microsoft.com/en-us/cpp/cpp/static-assert?view=vs-2019)
 |
Needs validation
 |
The terse form of static_assert is useful when the evaluated expression contains enough information that an additional message would be redundant.

Supported by all compilers. (VS2017.0)

Example:

static_assert(std::is_default_constructible_v<T>) is equally readable than static_assert(std::is_default_constructible_v<T>, "Must be default constructible")

 |

##
C++17 Library Features

Feature
 |
State
 |
Comments
 |

[std::variant](https://github.com/AnthonyCalandra/modern-cpp-features#stdvariant)
 |
Needs validation
 |
(Note: newly supported by PS4 SDK 7.0)
 |

[std::optional](https://github.com/AnthonyCalandra/modern-cpp-features#stdoptional)
 |
Needs validation
 |
(Note: newly supported by PS4 SDK 7.0)
 |

[std::any](https://github.com/AnthonyCalandra/modern-cpp-features#stdany)
 |
Disallowed
 |
Not supported on PS4 as of SDK 7.0 when RTTI is turned off.
 |

[std::string_view](https://github.com/AnthonyCalandra/modern-cpp-features#stdstring_view)
 |
Needs validation
 |
-
 |

[<functional>](https://en.cppreference.com/w/cpp/header/functional)
[https://github.com/AnthonyCalandra/modern-cpp-features#stdinvoke](https://github.com/AnthonyCalandra/modern-cpp-features#stdinvoke)

std::invoke, std::not_fn

 |
Needs validation
 |
-
 |

[<tuple>](https://en.cppreference.com/w/cpp/header/tuple)

std::apply, std::make_from_tuple

 |
Needs validation
 |
-
 |

[<type_traits>](https://en.cppreference.com/w/cpp/header/type_traits)

std::void_t, std::conjunction, std::disjunction, std::negation, std::invoke_result, std::is_invocable, std::bool_constant

 |

 |

 |

[std::filesystem](https://github.com/AnthonyCalandra/modern-cpp-features#stdfilesystem)
 |
Needs validation
 |
-
 |

[std::byte](https://github.com/AnthonyCalandra/modern-cpp-features#stdbyte)
 |
Needs validation
 |
-
 |

[Splicing for maps and sets](https://github.com/AnthonyCalandra/modern-cpp-features#splicing-for-maps-and-sets)
 |
Needs validation
 |
-
 |

[Parallel algorithms](https://github.com/AnthonyCalandra/modern-cpp-features#parallel-algorithms)
 |
Needs validation
 |
-
 |

##
C++14 Language Features

Feature
 |
State
 |
Comments
 |

[Binary literals](https://github.com/AnthonyCalandra/modern-cpp-features#binary-literals)
 |
Needs validation
 |
-
 |

[Generic lambda expressions](https://github.com/AnthonyCalandra/modern-cpp-features#generic-lambda-expressions)
 |
Needs validation
 |
Taking parameters by auto type makes lambda on-par with template functions. It is a great improvement to callbacks and generic algorithms that would be otherwise unnecessarily verbose. It also enables designs such as generic visitor pattern which wasn't possible without the feature.

The feature is supported by all compilers.

 |

[Lambda capture initializers](https://github.com/AnthonyCalandra/modern-cpp-features#lambda-capture-initializers)
 |
Needs validation
 |
-
 |

[Return type deduction](https://github.com/AnthonyCalandra/modern-cpp-features#return-type-deduction)
 |
Needs validation
 |
-
 |

[Decltype(auto)](https://github.com/AnthonyCalandra/modern-cpp-features#decltypeauto)
 |
Needs validation
 |
-
 |

[Relaxing constraints on constexpr functions](https://github.com/AnthonyCalandra/modern-cpp-features#relaxing-constraints-on-constexpr-functions)
 |
Needs validation
 |
The feature allows constexpr function to be written in almost identical style as normal run-time functions, improving readability and compile time.

Supported by all compilers.

 |

[Variable templates](https://github.com/AnthonyCalandra/modern-cpp-features#variable-templates)
 |
Needs validation
 |
-
 |

[[[deprecated]] attribute](https://github.com/AnthonyCalandra/modern-cpp-features#deprecated-attribute)
 |
Needs validation
 |
-
 |

##
C++14 Library Features

Feature
 |
State
 |
Comments
 |

[User-defined literals for standard library types](https://github.com/AnthonyCalandra/modern-cpp-features#user-defined-literals-for-standard-library-types)
 |
Needs validation
 |
-
 |

[Compile-time integer sequences](https://github.com/AnthonyCalandra/modern-cpp-features#compile-time-integer-sequences)
 |
Needs validation
 |
std::integer_sequence and std::index_sequence are useful template-metaprogramming tools that help transform variadic template arguments or constexpr array. Compilers usually implement the feature as magic intrinsics, which speeds up the compilation compared to the manually implemented recursive template.

Supported compilers - ?

 |

[std::make_unique](https://github.com/AnthonyCalandra/modern-cpp-features#stdmake_unique)
 |
Needs validation
 |
-
 |

[C++17 Language Features](#c-17-language-features)
[C++17 Library Features](#c-17-library-features)
[C++14 Language Features](#c-14-language-features)
[C++14 Library Features](#c-14-library-features)
