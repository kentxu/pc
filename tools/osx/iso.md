# OSX Utilities
<!-- TOC -->

- [OSX Utilities](#osx-utilities)
    - [Create OSX ISO](#create-osx-iso)
        - [Step by Step](#step-by-step)
        - [Streamlined script](#streamlined-script)
        - [Diskspace needed](#diskspace-needed)
    - [References](#references)

<!-- /TOC -->
## Create OSX ISO

### Step by Step
* First download the installerf from App Store, e.g. https://itunes.apple.com/us/app/macos-mojave/id1398502828?mt=12
* after the download is done, the installer app is temporarily placed in /Applications, e.g. “Install MacOS Mojave.app”
* create a temp DMG file to store the OS files
```
hdiutil create -o /tmp/Mojave -size 8500m -volname Mojave -layout SPUD -fs HFS+J
```

* mount DMG as a volume
```
hdiutil attach /tmp/Mojave.dmg -noverify -mountpoint /Volumes/Mojave
```

* use installer to create a install disk on the volume
```
sudo /Applications/Install\ macOS\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/Mojave --nointeraction
```

* detash volume to unmount the DMG
```
hdiutil detach /volumes/Install\ macOS\ Mojave

```

* Convert DMG to cdr
```
hdiutil convert /tmp/Mojave.dmg -format UDTO -o ~/Desktop/Mojave.cdr
```


* change CDR to ISO
```
mv ~/Desktop/Mojave.cdr ~/Desktop/Mojave.iso
```

### Streamlined script
```
osx=Catalina
hdiutil create -o /tmp/$osx -size 8500m -volname $osx -layout SPUD -fs HFS+J
hdiutil attach /tmp/$osx.dmg -noverify -mountpoint /Volumes/$osx
sudo /Applications/Install\ macOS\ $osx.app/Contents/Resources/createinstallmedia --volume /Volumes/$osx --nointeraction
hdiutil detach /Volumes/Install\ macOS\ $osx
hdiutil convert /tmp/$osx.dmg -format UDTO -o ~/Desktop/$osx.cdr
mv ~/Desktop/$osx.cdr ~/Desktop/$osx.iso
```

```
osx=Big Sur
boxsize=13000m
hdiutil create -o "/tmp/$osx" -size $boxsize -volname "$osx" -layout SPUD -fs HFS+J
hdiutil attach "/tmp/$osx.dmg" -noverify -mountpoint "/Volumes/$osx"
sudo /Applications/Install\ macOS\ $osx.app/Contents/Resources/createinstallmedia --volume "/Volumes/$osx" --nointeraction
hdiutil detach "/Volumes/Install macOS $osx"
hdiutil convert "/tmp/$osx.dmg" -format UDTO -o ~/"Desktop/$osx.cdr"
mv ~/"Desktop/$osx.cdr" ~/"Desktop/$osx.iso"
```

```
osx=Mojave
boxsize=6800m
hdiutil create -o "/tmp/$osx" -size $boxsize -volname "$osx" -layout SPUD -fs HFS+J
hdiutil attach "/tmp/$osx.dmg" -noverify -mountpoint "/Volumes/$osx"
sudo /Applications/Install\ macOS\ $osx.app/Contents/Resources/createinstallmedia --volume "/Volumes/$osx" --nointeraction
hdiutil detach "/Volumes/Install macOS $osx"
hdiutil convert "/tmp/$osx.dmg" -format UDTO -o ~/"Desktop/$osx.cdr"
mv ~/"Desktop/$osx.cdr" ~/"Desktop/$osx.iso"
```
### Diskspace needed
Mojave (10.14) 6800M
Catalina (10.15) 8500M
Bit Sur (11) 125000M


## References

https://osxdaily.com/2020/07/20/how-convert-macos-installer-iso/
