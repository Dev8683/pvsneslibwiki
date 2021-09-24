Here you will find detailed instructions for installing PVSnesLib on a Windows environment. 
 
To use it, you will need:  
  * msys  
  * Last version of DevKitSnes 
  * Last version of PVSnesLib binaries  
  * An editor like Programmer's Notepad, Sublime text or Eclipse (if your PC is strong enough ;-))  

Additional sections below will cover others OS installations like Linux and Mac OS X.  

Good luck!  

## Installing PVSnesLib on Windows

### Step 1: Installing the toolchain

#### DevkitSnes

The first thing you need to do to get you started is downloading the latest versions of devkitSNES and the tools that come with it. This is the core to all/most homebrew programs on the SNES, as it provides the C compiler and linker, and various tools.  

You can find the latest release here: [devkitsnes' latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

Put it wherever you like – it does not affect the compilation - but keep the path without any spaces.
We recommend however that you create the directory in **C:/snesdev**.

At this point, your folder must look like this:
```
  c:\snesdev
  .........\devkitSnes
  .................\bin
  .................\include
```

WARNING: Double check your files after you unzip (to avoid simple mistakes like this "c:\snesdev\devkitSnes\devkitSnes").

Then, you need to create a new environment variable PVSNESLIB_HOME to provide the path to this directory.
You can set PVSNESLIB_HOME to **/c/snesdev** by using this command line:
`setx PVSNESLIB_HOME "/c/snesdev"`, or you can set it manually like it is shown below:

![PVHome](https://www.portabledev.com/wp-content/uploads/2020/12/home_var.png)

Be careful: the path must be in Unix style (/c/ instead of c:\\) otherwise you will get build issues like "echo: command not found".

**WARNING!** Please remember that even though your folder path needs to be in "Unix style" you have to use your windows drive as your path start, for example, **/c/PVSneslibFolder**.
You will get issues like `LOAD_FILE_DATA: Could not open file "/usr/local/xxx.obj".` if you use the path like **/usr/local** because WLA does not support it.

#### Python

To use the c source code optimizer, you also need to have **Python** on your PC. Just download it from PortableDev website and install it in **c:\python27**.

<a id="python27" href="https://www.portabledev.com/wp-content/files/python-2.7.9.msi">Python 2.7</a>

If you put Python in another directory, just edit **816-opt.py** in **devkitSnes/bin** directory and change the first line to use the correct directory.  
```
  #!/c/Python27/python <- change here
  import sys
  import re
  import os
```

**WARNING!** _This point need to be tested and confirmed. Please keep us informed by discord if you tested it!_

Some people from the community get issues with the python part during the build process because they installed python only for the current user. It creates variables and profiles that PVSneslib does not recognize. Please choose the option "install for everyone on this system" to avoid issues.

#### Msys

We will need a Unix-like environment, so download **msys**  and extract it in your SNES directory. You will have a subdirectory named **msys** (C:\snesdev\msys) with all msys distribution in it.

<a id="msys1017" href="https://www.portabledev.com/wp-content/files/msys-1.0.17.exe">msys 1.0.17</a>

Msys needs to be added to Windows Path because lots of msys binary files are needed when we are going to compile.  

To add the **msys\bin** directory to your PATH environment variable (eg,  **c:\snesdev\msys\bin** in our example), right-click on the "Computer" icon, choose "Properties", and then "Advanced system settings". Click on the "Environment variables" button. 
 
I am French with a Windows 7 computer, so the names below will not reflect your exact configuration.

![Path](http://www.portabledev.com/wp-content/uploads/2018/02/pn_tools_04.jpg)

Choose the Path entry to add **c:\snesdev\msys\bin**.  

**WARNING!** _msys bin path MUST BE THE 1st ENTRY of your path to avoid using make from another location_

![Path2](https://www.portabledev.com/wp-content/uploads/2021/06/msyspath.png)

Some people have issues while they build samples from the repository because they installed 64b version of MinGW. To avoid these kinds of errors, please put msys bin path as the first entry of your path.

#### GCC 

Depending on the tools already installed on your computer, you may need to install GCC too.
For example, you will have to install it if you encounter this error building projects which use smconv tool (like the mario-like sample) :

![sm conv error](https://user-images.githubusercontent.com/981773/120016823-5e926300-bfe5-11eb-9ec3-c76223072ae0.png)

It is also necessary if you want to build yourself some tools in devkitsnes (like smconv !).

You can download the latest version of the tool [here](https://sourceforge.net/projects/tdm-gcc/) but we recommend you to get the 32 bit one, as we advised you for other tools!


#### Emulators  

Download emulators to test your homebrews and put them in the emulators directory (see unzipped devkitsnes, you will have the directory **C:/snesdev/emulators**).  

[bsnesplus beta](http://revenant1.net/bsnes-plus-benny-win64.zip)

[bsnesplus](https://github.com/devinacker/bsnes-plus/releases)

[no$sns](http://problemkaputt.de/sns.htm)

### Step 2: Installing the library PVSnesLib

Now download PVSnesLib library and unzip it in the same directory as your devkitSnes (eg, **C:/snesdev/pvsneslib** would be fine). You don't need to have PVSnesLib source code to use it, only obj files are needed.  

You can find the latest release here: [pvsneslib latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

It is also recommended that you install **‘snes examples’** (examples for PVSnesLib) and [Programmer's Notepad](http://www.pnotepad.org/download/) (an IDE), though they don’t necessarily affect the functionality of PVSneslib.

You can find the latest release here: [SNES examples latest release](https://github.com/alekmaul/pvsneslib/releases/latest)  

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
  ..................\docs
  .........\msys
  .........\snes-examples
  c:\python27
```

##### Let's start compiling with Programmer's Notepad

We will use the template example to test how our PVSnesLib library is installed. The template directory is shipped with PVSnesLib.  
