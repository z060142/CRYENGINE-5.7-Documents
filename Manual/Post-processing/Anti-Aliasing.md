# Anti-Aliasing

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/26872518
- Page ID: 26872518
- Breadcrumb: Post-processing > Anti-Aliasing
- Parent: Post-processing

## Content

##
Overview

A clean and stable image is very important for high-quality graphics. Furthermore, while there is a range of different anti-aliasing methods available, finding an efficient implementation and one that provides great quality remains one of the biggest challenges in rendering. This is even more true for VR applications, where jagged edges and crawling pixels can cause severe viewer discomfort and the rendering techniques employed have to operate within a very tight performance budget.

![Image](https://www.cryengine.com/docs/static/attachments/28265954)

##
Subpixel Morphological Antialiasing (SMAA) and Temporal AntiAliasing

SMAA is an efficient post-processing based technique that can reliably detect and smooth edges in an image. While it works very well in removing jaggies and staircase artifacts from edges, it does not solve the problem of temporal aliasing, where individual pixels and entire edges can flicker when in motion. To address those issues, CRYENGINE has pioneered the use of highly efficient temporal filters that take information from previous frames to improve the stability of subpixel features that would otherwise crawl and flicker in a very obvious way.

CVar/Command
 |
Description
 |

**
r_AntialiasingMode 1
**
 |
Enables SMAA without any temporal filtering.
 |

**
r_AntialiasingMode 2
**
 |
Enables SMAA with temporal filtering.
 |

**
r_AntialiasingMode 3
**
 |
Enables SMAA with temporal filtering and projection matrix jittering to further improve quality.
 |

##
Temporal Supersampling Antialiasing (TSAA)

TSAA slightly modifies the projection matrix in each frame to obtain more samples for any pixel over time. Since no extra pixels need to be rendered, the technique is highly efficient while at the same time being able to provide surprisingly good image quality - this makes it particularly suitable for console and VR applications, including PSVR. In fact, Robinson for PSVR shipped with Crytek's TSAA implementation and as introduced in CRYENGINE 5.4.

A particular focus of our TSAA implementation is to retain image sharpness (essential for VR applications), where and because of the perceived pixel size any visual artifacts are very noticeable.

While this technique generally works very well, there are some fail cases that can produce artifacts. One of the most obvious is the case of flickering edges, where the algorithm fails to properly classify samples from the previous frame as being valid. This issue can, to some degree, be mitigated with the use of the CVars listed below, but is unfortunately not always fully solvable.

CVar/Command
 |
Description
 |

**
r_AntialiasingMode 4
**
 |
Enables temporal supersampling (without SMAA).
 |

**
r_AntialiasingTSAAMipBias
**
 |
Sets mimap LoD bias for TSAA (negative values for sharpening).
 |

**
r_AntialiasingTSAASubpixelDetection
**
 |
Adjusts metric for detecting subpixel changes (higher: less flickering, but more ghosting).
 |

**
r_AntialiasingTSAASmoothness
**
 |
Adjusts smoothness of image under motion.
 |

##
Implementation Notes

TSAA is implemented as a post-processing technique analogous to the other SMAA modes.

Currently, TSAA uses an 8-bit sRGB for the history buffer, which is not sufficient for some high-contrast scenes. So to avoid persistent smearing artifacts the history buffer can be changed to 16 bit linear.
Currently, TSAA is applied in LDR after tone mapping, which means the history buffer will also contain motion blur output, resulting in relatively strong overall blurring under motion. So it's advisable to lower the motion blur shutter speed or if acceptable completely disable camera motion blur.

##
Supersampling

In addition to the efficient image-based AA techniques, CRYENGINE supports classic spatial supersampling for very high-quality rendering. Supersampling renders the scene at a higher resolution and downscales the image to obtain smooth and stable edges. Due to the high internal rendering resolution, supersampling is very performance heavy and is therefore only suitable for high-end PCs.

Cvar/Command
 |
Description
 |

**
r_SuperSampling 0/1
**
 |
Disables/enables supersampling.
 |

**
r_SuperSampling 2
**
 |
Enables 2x2 supersampling.
 |

**
r_SuperSampling 3
**
 |
Enables 3x3 supersampling.
 |

Supersampling can also be used in combination with the image-based AA techniques to further improve image quality.

[Subpixel Morphological Antialiasing (SMAA) and Temporal AntiAliasing](#subpixel-morphological-antialiasing-smaa-and-temporal-antialiasing)
[Temporal Supersampling Antialiasing (TSAA)](#temporal-supersampling-antialiasing-tsaa)
[Supersampling](#supersampling)
