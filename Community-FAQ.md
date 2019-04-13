The remaining entries here on the unofficial FAQ are maintained by the community.

# Frequently asked questions (FAQ)

**[Miscellaneous](#MiscSection)**

- [I want to contribute to this project ?](#MiscSection_1)
- [I want to ask something](#MiscSection_2)
- [I found a bug. What can i do ?](#MiscSection_3)
- [Can we create hirom game with the lib ?](#MiscSection_4)
- [Is it possible to rotate a picture ?](#MiscSection_5)
- [What is the function to clear text ?](#MiscSection_6)
- [How can i display special characters in text ?](#MiscSection_7)

**[Common errors](#CommonErrorsSection)**

- [What is CHECH_HEADERS error ?](#CommonErrorsSection_1)
- [Colors of my loaded picture are false](#CommonErrorsSection_2)
- [I get FIX_LABELS errror when i build my project](#CommonErrorsSection_3)

---

## <a name="MiscSection"/>Miscellaneous

### <a name="MiscSection_1"/>I want to contribute to this project ?

PVSneslib main developer and community will be happy! You can create a fork of this project and submit your code by pullrequest.

### <a name="MiscSection_2"/>I want to ask something

There is no more official forum for PVSneslib. The best thing to do is to ask on [Snesdev](https://forums.nesdev.com/viewforum.php?f=12) forum.

### <a name="MiscSection_3"/>I found a bug. What can i do ?

Please create a minimal code to reproduce it and store it on internet. Then you can create an issue on github explaining the bug.

### <a name="MiscSection_4"/>Can we create hirom game with the lib ?

No, PVSneslib currenty manage lorom games only.

### <a name="MiscSection_5"/>Is it possible to rotate a picture ?

Only background in mode7 can be rotate.

### <a name="MiscSection_6"/>What is the function to clear text ?

There is no function to clear text directly. You need to draw spaces on text instead.

### <a name="MiscSection_7"/>How can i display special characters in text ?

PVSneslib let you manage only characters from ascii code 32 to 127. If you need other characters, you need to implement it by yourself (and share it with the community !).
For more informations about text in PVSneslib, you can consult [this page](https://github.com/alekmaul/pvsneslib/wiki/Input-and-Output)

## <a name="CommonErrorsSection"/>Common errors

### <a name="CommonErrorsSection_1"/>What is CHECH_HEADERS error ?

Your game have to be build with sames parameters than we have in PVSnesLib header. This is because .obj files from the library are embedded with .obj files of you project which contains its own header too. It is an improvement to do !

### <a name="CommonErrorsSection_2"/>Colors of my loaded picture are false

It is an issue with your color palette. We do not recommend to use MS Paint which mix color strangly. You can use Graphics Gale software if you want to edit easily your colors. Don't forget : your transparency color must be the first in your palette. If it is not the case in Graphics gale, you can save palette directly, change content of the file to have your transparency color at first then load it and save your new image.

### <a name="CommonErrorsSection_3"/>I get FIX_LABELS errror when i build my project

It is recommended to separate your code in multiple files but do not declare global variables in .h files. Declare the variable within your source file, then use extern in other places (either .c files, or an .h file that .c files include).
