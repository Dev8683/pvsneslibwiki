Feel free to help us by implementing any of this functionalities !

# High priority:

- Include the python script directly in tcc tool
- upgrade to the latest version of tcc
- Review of constify tools :
	- '\_\_tcc_' should become 'tcc_'
	- manage const declared like : const myArray[5*6] = ...;
	- add a function to remove comments in C source file (// ou /* */)
	- add a function to detect include in C files then parse them
	- manage implicit declaration of const array (const char a[] = {3,3}) on one or multiple lines
- Add an example of how to update VRAM with a buffer (with, for example, two different screens)

# Medium priority:

- replace .obj files by .lib with wla dx
- Finish to implement mode 5, 6 by adapting gfx2snes to have compatible pictures (see [here](https://github.com/alekmaul/pvsneslib/issues/14))
- replace tasm.exe part (spc700) by the wla dx version to provide a unix alternative
- integrate docker image
- add some chipsets support (sa1, dsp, superfx, ...)
- harmonize tools bin2h.exe (devkitsnes) & bin2txt.exe (tools) to have the same name
- clean some issues opened for a long time on github
- create new sample to show how to load sounds and musics at the same time (we need to respect specific order: sound at first, then music...)
- replace pixel.c file by asm version to improve performances and provide function to draw pixels

# Low priority:

- Develop a more flexible asm sprite engine
- Develop a more flexible asm map engine
- Improve mode 7 camera rotation
- Add capabilities to create HIrom games
- Manage hblank
- develop new driver to get more files format with sound engine
- add new function getPaletteColor which will return the value from VRAM for the given color ID
- add in snes rules the check on PVSNESLIB_DEBUG variable. If it exists, it will create automatically the temporary tree to store all steps executed during the build (.ps file, .asp, .asm...). It will be easier and quick to see the content of each files to debug it.
- update in pvsneslib sources, samples code and tools which use extern variables the data type (probably char) by the real type (u16 for map/sprites...). It will avoid some cast in the code will be more clear
- add a new variable PVSNESLIB_DEBUG to provide detailed informations during the build process to assist users when they begin to use the library. For example: if you use setmode with mode7, display an error saying to use setmode7 function instead. It is a kind of assert wich could be managed in asm with .FAIL directive. By default, the library could be built without this variable and it will not decrease performances