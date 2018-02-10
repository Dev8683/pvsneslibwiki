# Day 1 - Installing a development environment

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

You can fin lastest release here: [devkitsnes latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

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

Download **msys** to use Unix like environment and extract it in you snes directory. (eg, ‘**C:\snesdev\**’ would be fine). You will have a subdirectory name **msys** with all msys distribution in it.  

[msys 1.0.17](http://www.portabledev.com/download/11/)

Msys need to be add to Windows Path because lot's of msys binary files are needed when we are going to compile.  

To add the **msys\bin** directory to your PATH environment variable (eg,  you will add  **c:\snesdev\msys\bin** in our example).  
I'm French with a Windows 7 computer, so the name will not reflect your exact configuration. The goal is to have the Windows Path textbox to add the msys/bin directory. Do a Right Click on Ordinateur" icon, choose "Paramètres système avancés" and then, click on "Variables d'environnement" button.  


{{:pn_tools_04.jpg?400}}

Choose the Path entrry to add **c:\snesdev\msys\bin** at the end of the line.  

{{:pn_tools_05.jpg?400}}
==== Emulators ====

Download emulators to test your homebrews and put them in the emulators directory (see unzipped devkitsnes, you will have the directory ‘**C:/snesdev/emulators**’).

[[http://byuu.org/bsnes/|Download bsnes]]

[[http://nocash.emubase.de/sns.htm|Download no$sns]]

===== Step 2: Installing the library PVSnesLib =====

Now download PVSnesLib library and unzip it in the same directory than your devkitSnes (eg, ‘**C:/snesdev/PVSnesLib**’ would be fine). You don't need to have PVSnesLib source code to use it, only obj files are needed.

[[currentversion_en|Download PVSnesLib]]

It is also recommended that you install **‘snes examples’** (examples for PVSnesLib) and [[http://www.pnotepad.org/download/|‘Programmer’s Notepad’]] (an IDE), though they don’t necessarily affect the functionality of libSnes.

[[currentversion_en|Download Snes examples]]

At the end, you must have something like that :
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

====== Let's start compiling with Programmer's Notepad ======

We will use template example to test how our PVSnesLib library is installed. The template directory is shipped with PVSnesLib.


==== Configuring tools ====

We will begin with a Programmer's Notepade Tools menu configuration to have the make command with **Alt+&** shortcut on our keyboard (but you are free to use something else :-D).
First of all, go to **Tools/Options** Menu and select Tools entry to the left. On the **Scheme** dropdown list, select **None** to have the "global tools" selections.

{{:pn_tools_01.jpg?nolink&400}}

Click on **Add** button to the right and type text as in the following screen.

{{:pn_tools_02.jpg?nolink}}

Do same thing for the **make clean** entry, you just have to add the word **clean** in **parameters** textbox, and add shorcut **Alt+é** on your keyboard (or what you want ;-)).
That's all, now you have the //make// and //make clean// command defined.

{{:pn_tools_03.jpg?nolink&400}}

==== Editing Path and compiling ====

With Programmer's Notepad menu **File/Open project(s)**, open the //template.pnproj// file that is in the psneslib **template** directory.
You will see 3 files on the Project Window.

  * hdr.asm is the file that defined the future snes rom definition.
  * Makefile is the file use to make the .sfc file.
  * template.c is the C source file.

Open **Makefile** and change the path to use the correct directory for your snesdev installation. Example below show a **D:/devperso/snesdevkit** root entry for my snes developments, if you have **c:\snesdev**, you just have to change it to **/c/snesdev**. Same thing for your devkitsnes entry.

<code make>
  # path to snesdev root directory (for emulators, devkitsnes, libsnes)
  export DEVKITSNES := /d/devperso/snesdevkit/
  
  # path to devkitsnes root directory for compiler
  export DEVKIT65XX := /d/devperso/snesdevkit/devkitsnes
</code>

Now, just do a //make clean// command (with the shortcut you configured below, for example Alt+é for me).
You must see a new Output window with the result of your make clean command.

<code typoscript>
  > "make" clean
  clean ...
  
  > Process Exit Code: 0
  > Time Taken: 00:00
</code>

If an error occurs, that's because your installation is not good, sorry about that. You can post your problem in our [[http://www.portabledev.com/smf/|PVSnesLib forum]], we will help you as soon as possible.

Ok, now your template directory is cleaned, you can run the //make// command (with shortcut, remember ).
You will have the following things in your Programmer's Notepad output window.

<code typoscript>> "make.exe" 
Compiling to .ps ... template.c
816-tcc -I/d/snesdev/devkitsnes/include   -I/d/snesdev/pvsneslib/include -I/d/snesdev/pvsneslib/template/  -Wall 
  -c template.c -o template.ps
Assembling ... template.ps
816-opt.py template.ps >template.asp 
optimization pass 1: 2 optimizations performed
optimization pass 2: 0 optimizations performed
2 optimizations performed in total
Moving constants ... template.ps
constify template.c template.asp template.asm
Done! Moved 0 variables (0 bytes)
Doing obj files ... template.asm
wla-65816 -io template.asm template.obj  
Doing obj files ... hdr.asm
wla-65816 -io hdr.asm hdr.obj  
Linking ... template.sfc
wlalink -dSno  template.obj hdr.obj /d/snesdev/pvsneslib/lib/crt0_snes.obj /d/snesdev/pvsneslib/lib/libc.obj 
  /d/snesdev/pvsneslib/lib/libm.obj /d/snesdev/pvsneslib/lib/libtcc.obj /d/snesdev/pvsneslib/template/template.sfc
template.obj: 1MEM_INSERT: Overwrite at $7fc8 (old $54 new $44).
template.obj: 1MEM_INSERT: Overwrite at $7fca (old $4d new $46).
template.obj: 1MEM_INSERT: Overwrite at $7fcb (old $50 new $41).
template.obj: 1MEM_INSERT: Overwrite at $7fcc (old $4c new $55).
template.obj: 1MEM_INSERT: Overwrite at $7fcd (old $41 new $4c).
template.obj: 1MEM_INSERT: Overwrite at $7fcf (old $45 new $20).
template.obj: 1MEM_INSERT: Overwrite at $7fd0 (old $20 new $43).
template.obj: 1MEM_INSERT: Overwrite at $7fd1 (old $20 new $41).
template.obj: 1MEM_INSERT: Overwrite at $7fd2 (old $20 new $52).
template.obj: 1MEM_INSERT: Overwrite at $7fd3 (old $20 new $54).
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc.asm: Section ".libc_misc" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc.asm: Section ".libc_cstd" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x0" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x1" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x2" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x4" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x5" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x6" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x7" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x8" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x9" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0xa" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0xb" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0xc" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0xd" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0xe" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0xf" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x10" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x11" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x12" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x13" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x14" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x15" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x16" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x17" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x18" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x19" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x1a" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x1b" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x1c" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x1e" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x1f" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x20" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x21" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x22" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x23" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x25" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x26" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x27" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x28" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x29" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x2a" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x2d" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x2e" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x2f" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x30" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x31" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x32" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x33" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x34" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x35" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x37" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x39" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x3a" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x3b" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x3c" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x3d" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x40" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x41" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x42" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x43" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x44" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x45" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x46" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x47" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x48" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x49" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libc.obj:libc_c.asm: Section ".text_0x4a" was discarded.
DISCARD: d:/snesdev/pvsneslib/lib/libm.obj:libm.asm: Section ".libm" was discarded.
/d/snesdev/devkitsnes/tools/snestools -hi! -ht"template" template.sfc

==============================
---snestools v0.1.0 20120525---
------------------------------
(c) 2012 Alekmaul 
==============================

File [template.sfc] has no header.

Change title to [TEMPLATE             ] ...
Change Checksum to 383Dh and Checksum complement C7C2h..
Done!
rm template.asm template.ps

> Process Exit Code: 0
> Time Taken: 00:01
</code>

That's all, you compiled your first program that can do nothing but it's a first step !. 

Welcome to PVSnesLib world and enjoy doing some homebrews for your Snes :-P !