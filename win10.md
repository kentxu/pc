<!-- TOC -->

- [Tools](#tools)
- [Git](#git)
- [CYGWIN](#cygwin)
- [Customize Sendto](#customize-sendto)

<!-- /TOC -->
## Tools
* enable long file path: Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem
* CYGWIN
    * wget,rsync,curl,zip,unzip,aria2c, git
* 7-zip
* VMWare Workstation
* Thunderbird
* Dictionary: Takaboto

## Git

```
git config --global user.name "John"
git config --global user.email "a@b.com"
git config --global core.autocrlf true
git config --global core.fileMode false
```

Unproven: not sure what the exactly value is needed for cygwin git and visual code (native win git). 


## CYGWIN
init user home structure, symlink or phyiscal dir

> e.g.  ln -s d:\temp ~/temp



## Customize Sendto
"Send to" is stored in C:\Users\Your Username\AppData\Roaming\Microsoft\Windows\SendTo

or  WMD+R and ```shell:sendto``` to open it

