# Commit Description Rules

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/25530492
- Page ID: 25530492
- Breadcrumb: CRYENGINE Build System > Commit Description Rules
- Parent: CRYENGINE Build System

## Content

Internally, CRYENGINE requires every commit made to the engine to follow a specific formatting. The following table lists all prefixes we use when submitting changes and should help you when you are referring to the source code:

Prefix
 |
Description
 |

**
!A
**
 |
New files added.
 |

**
!D
**

 |
Deleted files from the repository.
 |

**
!B
**
 |
Bugfix. this often includes the JIRA ticket ID corresponding to the bugfix. E.g.,
`
!B (Scaleform) (CE-5467) Fixed HUD updating slowly in medium & low spec
`

 |

**
!F
**
 |
A new feature has been implemented.
 |

**
!R
**
 |
The code has been refactored.
 |

**
!O
**
 |
Optimizations have been made.
 |

**
!T
**
 |
Tweaks or small parameter changes were made.
 |

**
!I
**

 |
Integration of files from/to a branch.
 |

**
!E
**

 |
This change is from an external contributor, e.g.,
`
!E David Kaye.
`
 |

**
!X
**
 |
This change will be excluded from the automated changelist generation. E.g.,
`
!XB (PS4) Release compilation.
`

 |

-
The general format for commit descriptions we follow is:
`
!Prefix (Component) (CE-5467) Fixed HUD updating slowly in medium & low spec.
`

-
Each "!" starts a new entry in the changelist, and so this is used to spread a description over multiple lines if necessary.

-
Combining prefixes is also possible. For example:

`
!XBO (Component) Fixed a bug that should be hidden from the changelist, and by the way, it optimizes the engine.
`
 In this case, the first occurring letter will be preferred during changelist creation.
