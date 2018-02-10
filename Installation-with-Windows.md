# Installing a development environment with Windows

You will find here detailed instruction for installing libSnes on Windows environment.  
To use PVSnesLib, you will need :  
  * msys  
  * Last version of DevKitSnes 
  * Last version of PVSnesLib binaries  
  * An editor like Programmer's Notepad or Eclipse (if your PC is strong enough ;-))  

Additional sections below will cover others OS installation like Linux and Mac OS X.  

Good luck!  

## Installing PVSnesLib on Windows

### Step 1: Installing the toolchain

#### DevkitSnes

The first thing you need to do to get you started is downloading the latest versions of devkitSNES and the tools that come with it. This is the core to all/most homebrew programs on the SNES, as it provides the C compiler and linker and various tools.  

You can find the lastest release here: [devkitsnes latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

Put it wherever you like – it doesn’t affect the compilation (you will only need to define it in your PATH), as long as you don’t extract it in a directory that contains spaces (eg, ‘**C:/snesdev/devkitSnes**’ would be fine).  

#### Python

To use c source code optimizer, you also need to have **Python** on your PC. Just download it from PortableDev website and install it in **c:\python27**.

[Python 2.7](http://www.portabledev.com/download/12/)

If you put Python in another directory, just edit **816-opt.py** in **devkitSnes/bin** directory and change first line to use the correct directory.  
```
  #!/c/Python27/python <- change here
  import sys
  import re
  import os
```

#### Msys

Download **msys** to use Unix like environment and extract it in you snes directory. (eg, **C:\snesdev\** would be fine). You will have a subdirectory name **msys** with all msys distribution in it.  

[msys 1.0.17](http://www.portabledev.com/download/11/)

Msys need to be add to Windows Path because lot's of msys binary files are needed when we are going to compile.  

To add the **msys\bin** directory to your PATH environment variable (eg,  you will add  **c:\snesdev\msys\bin** in our example).  
I'm French with a Windows 7 computer, so the name will not reflect your exact configuration. The goal is to have the Windows Path textbox to add the msys/bin directory. Do a Right Click on "Ordinateur" icon, choose "Paramètres système avancés" and then, click on "Variables d'environnement" button.  

![Path](http://www.portabledev.com/wp-content/uploads/2018/02/pn_tools_04.jpg)

Choose the Path entry to add **c:\snesdev\msys\bin** at the end of the line.  

![Path2](http://www.portabledev.com/wp-content/uploads/2018/02/pn_tools_05.jpg)


#### Emulators  

Download emulators to test your homebrews and put them in the emulators directory (see unzipped devkitsnes, you will have the directory **C:/snesdev/emulators**).  

[bsnesplus beta](http://revenant1.net/bsnes-plus-benny-win64.zip)

[bsnesplus](https://github.com/devinacker/bsnes-plus/releases)

[no$sns](http://problemkaputt.de/sns.htm)

### Step 2: Installing the library PVSnesLib

Now download PVSnesLib library and unzip it in the same directory than your devkitSnes (eg, **C:/snesdev/PVSnesLib** would be fine). You don't need to have PVSnesLib source code to use it, only obj files are needed.  

You can find the lastest release here: [pvsneslib latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

It is also recommended that you install **‘snes examples’** (examples for PVSnesLib) and [Programmer's Notepad](http://www.pnotepad.org/download/) (an IDE), thought they don’t necessarily affect the functionality of PVSneslib.

You can find the lastest release here: [snes examples latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

At the end, you must have something like that :  
```
  c:\snesdev
  .........\devkitSnes
  .................\bin
  .................\include
  .........\emulators
  .........\pvsneslib
  ..................\template
  ..................\include
  ..................\lib
  .........\msys
  .........\snes-examples
  c:\python27
```

##### Let's start compiling with Programmer's Notepad

We will use template example to test how our PVSnesLib library is installed. The template directory is shipped with PVSnesLib.  
