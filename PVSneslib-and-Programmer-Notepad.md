## Configuring tools

We will begin with a Programmer's Notepad Tools menu configuration to have the make command with **Alt+&** shortcut on our keyboard (but you are free to use something else :-D).
First of all, go to **Tools/Options** Menu and select Tools entry to the left. On the **Scheme** dropdown list, select **None** to have the "global tools" selections.

![PNT1](http://www.portabledev.com/wp-content/uploads/2018/02/pn_tools_01.jpg)

Click on **Add** button to the right and type text as in the following screen.  

![PNT2](http://www.portabledev.com/wp-content/uploads/2018/02/pn_tools_02.jpg)

Do same thing for the **make clean** entry, you just have to add the word **clean** in **parameters** text box, and add shortcut **Alt+é** on your keyboard (or what you want ;-)).  
That's all, now you have the _make_ and _make clean_ command defined.  

![PNT3](http://www.portabledev.com/wp-content/uploads/2018/02/pn_tools_03.jpg)

## Editing Path and compiling

With Programmer's Notepad menu **File/Open project(s)**, open the "template.pnproj" file that is in the psneslib **template** directory.  
You will see 3 files on the Project Window.  
* hdr.asm is the file that defined the future SNES ROM definition.
* Makefile is the file used to make the .sfc file.
* template.c is the C source file.

Now, just do a "make clean" command (with the shortcut you configured, for example Alt+é for me).
You must see a new Output window with the result of your make clean command.

```
  > "make" clean
  clean ...
  
  > Process Exit Code: 0
  > Time Taken: 00:00
```

If an error occurs, that's because your installation is not good, sorry about that. You can post your problem in our [Discord](https://discord.gg/VdG2rgwZ), here in [Issues Part](https://github.com/alekmaul/pvsneslib/issues), or [Portabledev Forum](http://www.portabledev.com/smf/index.php) (less active). We will help you as soon as possible.

Ok, now your template directory is cleaned, you can run the "make" command (with the shortcut, remember).
You will have the following things in your Programmer's Notepad output window.

```
> "make.exe" 
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
```

That's all, you've compiled your first program that does nothing but it's a first step !.  

Welcome to PVSnesLib world and enjoy doing some homebrews for your SNES :-P !