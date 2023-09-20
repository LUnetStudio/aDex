# LUnet aDex - Apache2 autoindex module extension
This is extension for Apache2 module **autoindex**. Autoindex automatically generates directories file lists in not so good looking format.

Extension **LUnet aDex** adds to these generated pages some styling and scripting and outputs pretty looking filelist with ability to show files details and previews and ability to instantly share that files.


## Features
- Modern design
- Files details - icon, size, modify time, description
- Preview panel for documents, images, audio and video files
- Social networks sharing button
- Customizable files icons and descriptions via custom text file - [see Custom descriptions](#custom-descriptions)


## Requirements
- Apache2 server with modules available:
  - autoindex
  - alias
  - include


## Installation
### Linux: from DEB package
Download and install .deb file:
```console
wget http://path/to/latest/libapache2-mod-adex_X.Y.ZZZZ.deb
sudo dpkg --install ./libapache2-mod-adex_X.Y.ZZZZ.deb
```
You will be asked for paths to apache2 modules-available and modules-enabled directories. Installation script will automatically made required symlinks to enable extension.

### Linux/Windows: from ZIP archive
1. Download .zip file and extract content in required directory (for example _/opt/aDex/_)
1. Open _/opt/aDex/module.conf_ and change path on lines 15 and 16 from ```"/usr/share/apache2/adex/"``` to your path where aDex was extracted (```"/opt/aDex/"```)
1. Locate apache2 modules directory where .load and .conf module files are stored (_/etc/apache2/mods-available_ for example)
1. Open Apache2 configuration file (mostly located somewhere at _/etc/apache2/apache2.conf_) and include necessary modules adding these lines:
```apache
Include /etc/apache2/mods-available/alias.load
Include /etc/apache2/mods-available/include.load
Include /etc/apache2/mods-available/autoindex.load
Include /opt/aDex/module.conf
```

> [!NOTE]
> Steps to configure/install aDex in Windows environment are the same, only locations of files will vary.


## Changelog
### v0.9.2309
- first released testing version


## To-Dos
- [ ] Fix preview box positioning on mobile devices


## ___________________________________________________________________________
### Custom descriptions
For adding basic descriptions to files in directory Apache mod_autoindex AddDescription directive is supported:
```apache
AddDescription "The planet Mars" mars.gif
AddDescription "My friend Marshall" friends/mars.gif
```

LUnet aDex offers easier way with more posibilities - just create text file structured as example below and save it into desired directory using filename _"!index"_:
```
apctest.output:		icon=/icons/console.png;  name=APCTest.output;	description=APC Test Output;
CairoSetup_64bit.exe:	icon=/icons/winexecutable.png;name=Cairo - Setup 64bit.exe;
icon_set.xcf:		icon=/icons/gimp.png;	description=Icons Set source;
Stray (2022).rar:	name=Stray Game.rar;	description=Meow Meow Meow;
w10default.deskthemepack:icon=/icons/desktop.png;description=Desktop Theme;
WinRAR_3.0.exe:		name=WinRAR 3.0;
WinRAR_6.02-x64.exe:	description=WinRAR Setup;

```
