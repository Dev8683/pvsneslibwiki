Feel free to help us by implementing any of this functionalities !

# High priority:

- TCC: integrate the last modifications done by mic_ **(Done: Alekmaul)**
- WLA DX upgrade: solve the warning which appear on consoles.asm and sprites.asm about the slot number **(Done: Alekmaul)**
- Review of the header file to include last modifications of wla **(Done: Alekmaul)**
- Remove DEVKITSNES and DEVKIT65XX to add them as environment variables (like JAVAHOME for example) **(Done: RetroAntho)**
- Include the python script directly in tcc tool
- upgrade to the latest version of tcc
- Review of constify tools :
	- '__tcc_' should become 'tcc_'
	- manage const declared like : const myArray[5*6] = ...;
	- add a function to remove comments in C source file (// ou /* */)
	- add a function to detect include in C files then parse them
	- solve the issue from big size array : https://github.com/alekmaul/pvsneslib/issues/18 (sample available in attachment)
	- manage implicit declaration of const array (const char a[] = {3,3}) on one or multiple lines

# Medium priority:

- recursively scan for source code in Makefile **(InProgress: RetroAntho)**
- replace .obj files by .lib with wla dx
- Finish to implement mode 5, 6 by adapting gfx2snes to have compatible pictures (see [here](https://github.com/alekmaul/pvsneslib/issues/14))
- replace tasm.exe part (spc700) by the wla dx version to provide a unix alternative
- integrate docker image
- add a vscode template
- add some chipsets support (sa1, dsp, superfx, ...)
- tcc : review the part which create unique file name which add a slah on unix system

# Low priority:

- Develop a more flexible asm sprite engine
- Develop a more flexible asm map engine
- Improve mode 7 functionalities and include the sample provided by [mills32](https://github.com/alekmaul/pvsneslib/issues/24)
- Add capabilities to create HIrom games
- Manage hblank
- develop new driver to get more files format with sound engine
- add new function getPaletteColor which will return the value from VRAM for the given color ID