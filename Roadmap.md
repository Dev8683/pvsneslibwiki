Feel free to help us by implementing any of this functionalities !

# High priority:

- WLA DX upgrade: solve the warning which appear on consoles.asm and sprites.asm about the slot number
- Review of the header file to include last modifications of wla
- Remove DEVKITSNES and DEVKIT65XX to add them as environment variables (like JAVAHOME for example) 
- replace .obj files by .lib with wla dx
- TCC: integrate the last modifications did my mic_
- Include the python script directly in tcc tool
- upgrade to the latest version of tcc

# Medium priority:

- Finish to implement mode 5, 6 by adapting gfx2snes to have compatible pictures (see [here](https://github.com/alekmaul/pvsneslib/issues/14))
- replace tasm.exe part (spc700) by the wla dx version to provide a unix alternative
- integrate docker image

# Low priority:

- Develop a more flexible asm sprite engine
- Develop a more flexible asm map engine
- Improve mode 7 functionalities and include the sample provided by [mills32](https://github.com/alekmaul/pvsneslib/issues/24)
- Add capabilities to create HIrom games
- Manage hblank
- develop new driver to get more files format with sound engine