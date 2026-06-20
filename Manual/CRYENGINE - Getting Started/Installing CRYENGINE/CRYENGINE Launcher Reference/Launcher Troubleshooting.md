# Launcher Troubleshooting

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36870268
- Page ID: 36870268
- Breadcrumb: CRYENGINE - Getting Started > Installing CRYENGINE > CRYENGINE Launcher Reference > Launcher Troubleshooting
- Parent: CRYENGINE Launcher Reference

## Content

Below is a collection of tips and tricks to help remedy common issues faced when downloading/installing the CRYENGINE Launcher.

For issues not covered in the sections below, please reach out to the CRYENGINE team through its  or
[Support](https://www.cryengine.com/support)
 channels with a complete description of the problems faced.

Before troubleshooting, please ensure that all installation instructions have been followed correctly.

Some of the troubleshooting solutions below involve making changes to the operating system, hence should only be carried out by experienced users that are aware of the risks involved.

Users might need to expose 'hidden folders' if those listed below cannot be found.

##
Slow Download Speeds

To improve download speeds:

-
Expose the Launcher and the Engine executable to the firewall.

-
White-list the Launcher and Engine on installed Anti-Virus software.

-
Flush and reset the DNS cache according to the following instructions:
OS
 |
Instructions
 |

**
Windows 10
**
 |

-
Hold down the
**
Windows
**
 key and press the
**
X
**
 key to open the Power User Menu.

-
Click the Command Prompt (Admin) / Windows PowerShell (Admin) option from the Menu.

-
Within Command Prompt/Windows PowerShell, type the following:

-
`
ipconfig /flushdns
`
 then press
**
Enter
**
.

-
`
ipconfig /registerdns
`
 then press
**
Enter
**
.

-
`
ipconfig /release
`
 then press
**
Enter
**
.

-
`
ipconfig /renew
`
 then press
**
Enter
**
.

-
`
netsh winsock
`
reset then press
**
Enter
**
.

-
Reboot the system.
 |

**
Windows 8
**
 |

-
Navigate to the desktop.

-
Hold down the
**
Windows
**
key and press the
**
R
**
 key to open the Run window.

-
Type
`
cmd
`
 within the Run window and press
**
Enter
**
 to open the Command Prompt.

-
Within Command Prompt, type the following:

-
`
ipconfig /flushdns
`
 then
press
**
Enter
**
.

-
`
ipconfig /registerdns
`
*

*
then
*

*
press
**
Enter
**
.

-
`
ipconfig /release
`
*

*
then press
**
Enter
**
.

-
`
ipconfig /renew
`
 then press
**
Enter
**
.

-
`
netsh winsock
`
*

*
`
reset
`
then
*

*
press
**
Enter
**
.

-
Reboot the system.
 |

**
Windows 7
**

 |

-
Hold down the
**
Windows
**
key and press the
**
R
**
key to open the Run window.

-
Type
`
cmd
`
within the Run window and press
**
Enter
**
 to open the Command Prompt
**
.
**

-
Within Command Prompt, type the following:

-
`
ipconfig /flushdns
`
 then press
**
Enter
**
.

-
`
ipconfig /registerdns
`
*

*
then press
**
Enter
**
.

-
`
ipconfig /release
`
*

*
then press
**
Enter
**
.

-
`
ipconfig /renew
`
 then press
**
Enter
**
.

-
`
netsh winsock
`
*

*
`
reset
`
then press
**
Enter
**
.

-
Reboot the system.
 |

DNS

-
For more information on re-configuring network settings to use
**
Google's Public DNS
**
, please refer to Google's article
[here](https://developers.google.com/speed/public-dns/docs/using)
.

-
For more information on
**
Cisco's OpenDNS
**
, please refer to Cisco's guide
[here](https://www.opendns.com/setupguide/)
.

-
For more information on
**
Cloudflare's DNS
**
, please refer to the Cloudflare documentation
[here](https://developers.cloudflare.com/1.1.1.1/setup/windows/)
.
[Slow Download Speeds](#slow-download-speeds)
