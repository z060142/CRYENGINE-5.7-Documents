# User Experience Guidelines

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873248
- Page ID: 26873248
- Breadcrumb: CRYENGINE Sandbox Programming > User Experience Guidelines
- Parent: CRYENGINE Sandbox Programming

## Content

##
Overview

*
"UI is important because it affects the feelings, the emotions and the mood of your users. If the UI is wrong and the user feels like they cannot control your software, they literally would not be happy and they will blame it on the software. If the UI is smart and things work the way the user expected them to work, they will be cheerful as they manage to accomplish small goals.
*

*
To make people happy you have to let them feel like they are in control of their environment. To do this, you need to correctly
*

*
interpret their actions. The interface needs to behave in the way they are expecting it to behave.
*

*
Thus, the cardinal axiom of all user interface design:
*

*
A user interface is well-designed when the program behaves exactly how the user thought it would."
*

These guidelines have been designed so that anyone can read about, understand the philosophy and the thought processes that Programmers and Workflow Designers need to follow in order to create a better and more consistent user experience throughout our suite of tools.

The target audience is mostly Tools Programmers, as they use these guidelines as a basis to review the tools that are being developed. We recommend reading these guidelines before you start working on a new tool as it will help you during your design process, but also to use it as a checklist while iterations take place - this will ensure your tool fits in with the overall design philosophy.

These guidelines will be expanded upon as we see fit and as new trends emerge.

##
Design Pillars

We want a user experience that is …

##
Intuitive

-
Can a feature be discovered by the user? How easy is it to find?

-
Menus, Contextual menus and tooltips are good solutions to show the user the correct way.

-
Use direct manipulation of objects (edit in Viewport, gizmos, drag and drop) rather than the "select object, invoke action" approach. The former interactions are more efficient and more intuitive.

-
Strive for a
**
 UI that self-documents
**
 over the need for extensive documentation or tutorials.

-
Tooltips, but also Commands, Nodes or Console Variables that have auto-generated UI's that document their usage.

-
Design for everyone, not just your expert users: optimize for your "intermediate" users and the major use case.

-
Remember that expert users are already used to your system and often will not provide you with the best solution to their problem.

-
User-centric design: focus on a
**
solution for the user's problem
**
,
**
not on a feature for the sake of
**
**
itself.
**

-
Put yourself in the user's shoes, in their thought process, analyze their goals and needs, verbalize the need from a user perspective.

-
Expose your feature in order to best fit the user's goal in this particular context.

-
A vast collection of features does not constitute a good tool, while the same features in the right places and exposed in the right way would be.

-
UI Language should be akin to
**
a conversation
**
 with the user, not just a reflection of the code.

-
Use real life metaphors. Examples are the "trash bin" or the "clipboard".

-
Make use of
**
personalization
**
 over customization: let the UI learn from the user and adapt.

-
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873106](
Sandbox Personalization Page
)

-
[http://www.towerdata.com/blog/2012/02/22/personalization-vs-customization-2](
Towerdata: Personalization vs. Customization
)

##
Immersive

-
**
WYSIWYG
**

-
Every action has
**
immediate feedback
**

-
Reduce all distractions

-
No questions,
**
don't interrupt
**
 the user

-
Performance is the universal UX killer: noticeable performance drops on the UI thread are not allowed -
**
use multi-threading
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873110](
Sandbox Threading API
)
**
**

-
**
Stability:
**
 no crashes allowed, always recover from errors when possible

-
No need to use external applications beyond the main content authoring tool for that workflow (DCC, Audio Middleware…). This means no Windows Explorer, p4v, Notepad, 7zip …

-
Reduce context switches  both within the application and with external applications.
**
keep the user focused
**

##
Consistent

-
Aesthetic consistency and user experience consistency throughout the whole app

-
Professional look and feel

-
Familiar UI elements are reused, which create confidence in the program

-
Consistent with established standards: Windows, DCC tools and state of the art tools

-
Less is more:
**
Reduce the number of concepts
**
, make the ones you keep very well defined, don't let two concepts compete with each other. This increases both consistency and learnability.

##
Fast to Iterate

-
Increases overall
**
efficiency
**
 by a large margin

-
Less frustration, more
**
productivity
**

-
More iterations yield better
**
quality
**
 results

-
Forgiveness: experimenting with the software and destructive actions should not slow down iteration (since you have to undo or can cancel all your changes)

-
Iteration time concerns include:

-
Console and other target platform's iteration time

-
Programmer iteration time to work within the system

-
Build system iteration time

-
Time before a change is propagated to everyone for collaborative workflow

##
Powerful

-
Expose as much functionality as makes sense to the user within existing frameworks (such as node systems or component-based systems)

-
Makes the application more
**
versatile
**
 but still
**
familiar
**

-
Encourages exploration and experimentation

-
Prefer data driven systems which:

-
Reduces interdependency between Programmers and users

-
Enables work in parallel, where the user is not blocked waiting for a feature

-
And where the Programmer is not waiting for the Designers' specification

-
Prefer to rely on open standards and exchange formats to enable
**
compatibility
**
 with most existing software and tools

-
**
Enable the user, do not restrict.
**
 Let users make their own decisions. Avoid:

-
Arbitrary technical constraints

-
Hardcoded naming conventions

-
Expectations on disk file structure

-
Dependency on a particular software (middleware or 3
rd
 party app, especially DCC)
These design pillars should stay present in your mind at every step of the way, from design to the implementation of your tools. Every decision and every aspect of the tools we make should reflect our user experience philosophy.

##
UI Guidelines

To comply with CRYENGINE standards our tools need to fulfill these guidelines as well as Windows UX Guidelines (links to follow) which cover a lot more than this document can. Our main development platform is Windows, so it is important that the User Experience is optimized for it, even though other platforms matter as well.

Here is a concise list of guidelines for a tool to fit in with our philosophy and direction for the UX. We will use these to define our own standards, and it is therefore important that every Programmer knows about these requirements.

Ideally, involve the Sandbox Design Group as early as possible in the development of your tool. They will help you with design and implementation and help you to make the right choices from the very beginning!

##
General

-
Every tool is
**
usable as is
**
 to achieve the main use case and without extra configuration or documentation

-
UI is
**
always responsive
**

-
Every UI action has
**
feedback
**
, failure should be clearly communicated:
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873104](
Notifications and Error Reporting
)

-
Every state of the tool can be easily accessed and without repeating the commands that led to the state the first time

-
Heavy processing is done by a thread - there is a notification to the user for when the task starts, is in progress and when it ends
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873110](
Sandbox Threading API
)
**

-
When applicable, links to
**
help and tutorials
**
 should be provided. In-Editor help can be created using
**
tooltips
**
 or the
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/26875311](
Help System
)
**

-
Are all expected UI interactions available?

-
Does the contextual popup menu give access to all possible actions on the selected object?

-
Things that look selectable should be selectable

-
Things that look drag&droppable should be

-
Copy/cut/paste work as expected

-
Undo/Redo/Add/delete/rename...

-
Are tooltips present?

##
Controls

-
**
All controls are standard.
**
Do not make new controls, exceptions need a strong justification. Exotic controls are not desirable.

-
The best control to present the data type is used

-
Range or choice of values is clear and understandable at first glance

-
Bad: 0-255, Good: 0%-100%

-
Use real life units where applicable and show them in the UI

-
**
Values are validated
**
 before an input is accepted, no error state or crash is possible by "injection". Regex validation is good practice.

-
All controls have
**
tooltips
**

-
**
Use progressive disclosure
**
, such as collapsible frames to mask the advanced controls to novice and intermediate users. Identify which parameters need to be exposed to the most common use case. It is good practice to save the state of progressive disclosure in personalization, so the next usage will return to what the user did last.

##
Text and Language

-
**
User-centric vocabulary
**
 is used

-
Example: Use degrees instead of Radian

-
Use real world metaphors and conversation-like language instead of technical terms

-
Menu names are one word only

-
Menu actions that open dialogs end with "…"

-
Menu actions are capitalized properly. All words have upper case first letter except connection words (to, for …).

-
**
All strings must be translated
**

-
Style and Tone:
[https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477(v=vs.85).aspx](
Microsoft Windows - Style and tone
)

-
Detailed guidelines:
[https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478(v=vs.85).aspx](
Microsoft Windows - User interface text
)

##
Messages

-
**
[/docs/static/engines/cryengine-5/categories/23756813/pages/26873104](
Notifications
)
**
are the primary form of messaging to the user

-
**
No modal dialogs
**
 (exceptions need strong justification)

-
Questions must have a "do not show again" box (personalization)

-
Do not ask a question if you don't need an answer immediately!

-
If informing the user, use notifications not a modal dialog

-
If the question can be answered later do not use a dialog

-
Error messaging is properly conveyed

-
**
No spamming
**
 the log or notifications

-
Errors should be shown within the main working UI element if possible

-
Error messaging should provide hints towards a solution

-
If possible, error messages should provide an interactive "link" to the problem area

##
Commands

-
**
All actions
**
 are available in
**
menus
**
, toolbars and shortcuts

-
All actions are available for
**
python
**
 scripting

-
All actions are internally calling a
**
command
**

-
All commands implement
**
undo/redo
**
 when applicable

-
All commands are
**
documented
**
 from code

##
Shortcuts

-
There is a common logic behind setting shortcuts to actions. When you design the default shortcut for your actions make sure that they follow this logic as much as possible. While not a hard rule it makes things much more consistent

-
**
Ctrl
**
 is commonly used to signify a command and should be the
**
default modifier
**
 key for your shortcut unless it is already used with the same key. In this case, try to find another relevant key before thinking about using another modifier

-
**
Alt
**
 is commonly used to access an action that is very similar, it offers an
**
alternate behavior
**
 to the same shortcut without alt

-
**
Shift
**
 is commonly used to
**
invert an action
**
: if H is hidden, then Shift+H should be shown and not Ctrl+H. Shortcuts are rarely only "Shift+key" unless "key" is already a shortcut

-
**
Win/Meta
**
 key is commonly used to signify a shortcut that is handled by the
**
OS
**
 and transcends application context

-
**
Do not override standard shortcuts
**
 for something else: Freeze should not be "Ctrl+F" as it is the standard for Find, Clone should not be "Ctrl+C" as that is the standard for Copy.

##
Selection

Selection and deselection behavior must be implemented according to standard behaviors which are common to most OS, platforms and software. However, due to our more complex selection models we have designed a more global approach.

For
**
list-based
**
 selection. In general when using Qt's selection behaviors use "
**
ExtendedSelection
**
" mode.

-
**
SHIFT + left mouse click
**
 selects between last selected and clicked item

-
**
CTRL + left mouse click
**
toggles the current state of selection of the clicked item
For
**
drag-selections
**
 (also called rectangle selection, marquee selection)

-
**
SHIFT + drag-select
**
 adds items to the selection

-
**
CTRL + drag-select
**
toggles selected state of items

-
**
ALT + drag-select
**
removes items from selection

##
Final Checklist

-
All UI behaviors should relate to an established standard (exceptions need a strong justification)

-
No duplication of UI components that could otherwise have been unified or reused

-
Settings are correctly split between a window's local settings and the app's global settings

-
Personalization is integrated and its settings are persistent

-
Help system (F1) is integrated and directs to the relevant information/wiki page

-
There aren't any hidden behaviors or modifiers that someone has to know, but the UI doesn't expose

-
Example: Ctrl-Drag differs from normal Drag unless there is a hint in tooltip or the action is available in other parts of the UI

-
UI has been Reviewed by the Sandbox Design Group and a selected group of target users

##
Visual Guidelines

##
Theme

-
Fonts and colors should be using the theme, no hard coding

-
Use bold sparingly

-
A large percentage of the population is color-blind. Rely on shape more than color, use a strong contrast

##
Icons

-
Are kept minimal, do not rely on icons too much

-
All actions available by icons should be available in menus

-
Are consistent with both the Sandbox's icon library and established standards of iconography

##
Layout

-
Aesthetically pleasing layout and proportions

-
Effective layout in regards to the user's workflow
[https://msdn.microsoft.com/en-us/library/windows/desktop/dn742486(v=vs.85).aspx](
Microsoft Windows - Layout
)

-
Reusing familiar UI components

-
Less is more: no more widgets than are necessary, rather pack in more functionality in fewer widgets

-
If you are making a custom layout you are probably doing something wrong

-
If your tool needs space to scroll, then it is better if your tool has a vertical rather than a horizontal layout. A vertical layout is more intuitive and has better controls due to page up/down keys and the mouse wheel. As with everything, there are exceptions such as timeline-based views

##
Common Mistakes

We wanted to list the most common mistakes and anti-patterns that have been observed in CRYENGINE in order to make everyone aware of it and hopefully correct their bad habits. This list will be expanded as we discover new common anti-patterns in our codebase.

-
**
The log is not a tool to communicate with the user, it is only a Developer and debug tool.
**
Use notifications if the user really needs to be notified.

-
**
Do not copy-paste
**
 a tool because it looks similar. Build better and faster from scratch.

-
Tree views are a good view, but above 3 levels of depth is too much and should prompt a redesign. This applies to property trees.

-
**
Reflection is not enough
**
. The layout of our data structure (s) is designed to be practical from a coding perspective and not for the user experience. Choose appropriate display names for your variables. Convert them to a better unit/range if necessary. Expose enum values with clear names. Group variables semantically and use progressive disclosure.

-
More options do not make the tool more usable.

-
Text should never have to be cut in the default layout of your tool when the app is maximized. In general when the app is maximized and the tool is given the intended area, then there should not be any scrolling or cropping.

-
UI elements should not move, users should always know where to expect to find something.

-
**
Avoid long baking times.
**
 Provide a way to get a preview with a short iteration time even though the best result might need baking. It shouldn't be necessary to wait for iteration.

-
Do not ask for confirmation for actions that have an undo. Only irreversible actions should have confirmation. (i.e. no confirmation for deleting something in the level for instance).

##
Addendum

There are many ways that we can improve the user experience of our tools and there are many methods at our disposal that are beyond the scope of these guidelines. Do not hesitate to fall back on proven methods of designing a better user experience when you feel the need.

These tools and methods include:

-
Paper mockups

-
Mental models

-
Tracking metrics and analytics

-
A/B testing

##
More Information

If you are looking for more detailed information on how a UI component should look, or to read more on UX design and guidelines that are used to build state of the art desktop applications, then please refer to the following links:

-
Microsoft Windows (Design principles):
[https://msdn.microsoft.com/en-us/library/windows/desktop/dn742491(v=vs.85).aspx](
Microsoft Windows - Windows UX design principles
)

-
Microsoft Windows (Simple and powerful UI):
[https://msdn.microsoft.com/en-us/library/windows/desktop/dn742462(v=vs.85).aspx](
Microsoft Windows - How to design a great user experience for desktop applications
)

-
Microsoft Windows (UX Checklist):
[https://msdn.microsoft.com/en-us/library/windows/desktop/dn742479(v=vs.85).aspx](
Microsoft Windows - UX checklist for desktop applications
)

-
Apple OSX:
[https://developer.apple.com/library/mac/documentation/UserExperience/Conceptual/OSXHIGuidelines/](
Apple - Human Interface Guidelines
)
Windows UX guidelines in particular apply to the Sandbox, as Windows is the main platform of development for CRYENGINE.

[#design-pillars](
Design Pillars
)
[#ui-guidelines](
UI Guidelines
)
[#visual-guidelines](
Visual Guidelines
)
[#common-mistakes](
Common Mistakes
)
[#addendum](
Addendum
)
[#more-information](
More Information
)
