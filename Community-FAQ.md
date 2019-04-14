The remaining entries here on the unofficial FAQ are maintained by the community.

# Frequently asked questions (FAQ)

**[Miscellaneous](#MiscSection)**

- [I want to contribute to this project](#MiscSection_1)
- [I want to ask something](#MiscSection_2)
- [I found a bug. What can i do ?](#MiscSection_3)
- [Can we create hirom game with the lib ?](#MiscSection_4)
- [Where comes from PVSnesLib name ?](#MiscSection_5)

**[About the lib](#AboutPVsneslib)**

- [Is it possible to rotate a picture ?](#AboutPVsneslib_1)
- [What is the function to clear text ?](#AboutPVsneslib_2)
- [How can i display special characters in text ?](#AboutPVsneslib_3)
- [How to create random number ?](#AboutPVsneslib_4)
- [What is the goal of each tool ?](#AboutPVsneslib_5)

**[Common errors](#CommonErrorsSection)**

- [What is CHECH_HEADERS error ?](#CommonErrorsSection_1)
- [Colors of my loaded picture are false](#CommonErrorsSection_2)
- [I get FIX_LABELS errror when i build my project](#CommonErrorsSection_3)
- [Can i load sprites in 0x0000 ?](#CommonErrorsSection_4)
- [Why HDMA channel 0 doesn't work ?](#CommonErrorsSection_5)

---

## <a name="MiscSection"/>Miscellaneous

### <a name="MiscSection_1"/>I want to contribute to this project

PVSneslib main developer and community will be happy! You can create a fork of this project and submit your code by pullrequest.
If you want to create or update wiki pages, you can do it directly. Wiki pages are more pleasant with pictures and illustration but github requires to give a link. To avoid to lost pictures in a future if it is store anywhere on internet, you can use [this page](https://github.com/alekmaul/pvsneslib/issues/26) especially did for it. To upload your image, just add a comment, copy/paste it and copy hyperlink created.

### <a name="MiscSection_2"/>I want to ask something

There is no more official forum for PVSneslib. The best thing to do is to ask on [Snesdev](https://forums.nesdev.com/viewforum.php?f=12) forum.

### <a name="MiscSection_3"/>I found a bug. What can i do ?

Please create a minimal code to reproduce it and store it on internet. Then you can create an issue on github explaining the bug.

### <a name="MiscSection_4"/>Can we create hirom game with the lib ?

No, PVSneslib currenty manage lorom games only.

### <a name="MiscSection_5"/>Where comes from PVSnesLib name ?

This tool could not be named LibSnes because an other project with same name was already existing. 
The "PV" letters is a tribute to PocketViewer, the famous Casio diary on which Alekmaul has developped there are a long time !

---

## <a name="AboutPVsneslib"/>About the lib

### <a name="AboutPVsneslib_1"/>Is it possible to rotate a picture ?

Only background in mode7 can be rotate.

### <a name="AboutPVsneslib_2"/>What is the function to clear text ?

There is no function to clear text directly. You need to draw spaces on text instead.

### <a name="AboutPVsneslib_3"/>How can i display special characters in text ?

PVSneslib let you manage only characters from ascii code 32 to 127. If you need other characters, you need to implement it by yourself (and share it with the community !).
For more informations about text in PVSneslib, you can consult [this page](https://github.com/alekmaul/pvsneslib/wiki/Input-and-Output)

### <a name="AboutPVsneslib_4"/>How to create random number ?

If you want to create random numbers, you can use rand() function available in PVSnesLib. You do not need to initialise something, it is managed by the library.
rand() function will works only if you assigned its result to u16 variable type.
To limit numbers between values like 0 and 50, you have to do (rand() % 50). But keep in mind that modulos, multiplications and division operations are very very slow on 65C816 processor used by Snes and try to avoid using it when possible.

### <a name="AboutPVsneslib_5"/>What is the goal of each tool ?

- bin2txt : convert binary file (like an image) to text file to include it directly in your project

- gfx2snes : transform all kinds of graphics to resources in Super Nintendo format. This is a central tool used by PVSneslib to load sprites, maps or palettes.
Remember you that we have a lot of constraints on Snes and each parameter of the tool is important ! Parameters are divided in 3 groups :
	G for Graphics
	M for map
	P for palettes

- smconv : to covert musics or sounds to bank of sounds readable on Super Nintendo and its sound processor SPC700

- snesbrr : to convert .wav files to .brr. If you want more informations on this format, you can read [this page](https://wiki.superfamicom.org/bit-rate-reduction-(brr))

- snestools : this tool give us capabilities to patch the rom after its build. Currently, you can change country (so PAL/NTSC), title of your game and usage or not of ram. You will see it in all Makefiles of project.

- 816-tcc and 816-opt.py : this is the tiny C compiler for 8/16 archicture. Due to some limitations and performances issues, a python script is used after to optimized produced code.

- bass : ...to complete...

- bin2h : to convert binary file. Maybe is it double with bin2txt ?

- constify : ...to complete...

- stripcom : ...to complete...

- tasm : ...to complete...

- wla-65816 and wlalink : these tools are assembler to convert your .asm files to .obj files (code readable by 65c816). Wlalink is the linker that "merge" all files.

---

## <a name="CommonErrorsSection"/>Common errors

### <a name="CommonErrorsSection_1"/>What is CHECH_HEADERS error ?

Your game have to be build with sames parameters than we have in PVSnesLib header. This is because .obj files from the library are embedded with .obj files of you project which contains its own header too. It is an improvement to do !

### <a name="CommonErrorsSection_2"/>Colors of my loaded picture are false

It is an issue with your color palette. We do not recommend to use MS Paint which mix color strangly. You can use Graphics Gale software if you want to edit easily your colors. Don't forget : your transparency color must be the first in your palette. If it is not the case in Graphics gale, you can save palette directly, change content of the file to have your transparency color at first then load it and save your new image.

### <a name="CommonErrorsSection_3"/>I get FIX_LABELS errror when i build my project

It is recommended to separate your code in multiple files but do not declare global variables in .h files. Declare the variable within your source file, then use extern in other places (either .c files, or an .h file that .c files include).


### <a name="CommonErrorsSection_4"/>Can i load sprites in 0x0000 ?

Yes, you can do it but remember that PVSneslib text management use begin at 0x0000. So if you want to use font system provided with the library, you need to begin after.

### <a name="CommonErrorsSection_5"/>Why HDMA channel 0 doesn't work ?

HDMA channel 0 is used internally for all DMA functions.
