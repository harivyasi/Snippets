# Installing DFT-D3 package on Windows

These instructions are for installing (compiling) DFT-D3 on Windows 10. The
plan is to use the GNU Fortran Compiler to do the same.

## Steps
1. Download and extract the DFT-D3 package's tarball from its
[webpage](https://www.chemie.uni-bonn.de/pctc/mulliken-center/software/dft-d3/). 
Put the extracted tarball in a sensible place where you can find it again
(i.e. move it out of the `Downloads` folder).

2. [GNU Fortran compiler](https://gcc.gnu.org/wiki/GFortran) is [available for
Windows](https://gcc.gnu.org/wiki/GFortranBinaries) via the
[MinGW-w64](http://mingw-w64.sourceforge.net/) project. One can [download the
binary](http://mingw-w64.org/doku.php/download) for Windows from
[here](http://mingw-w64.org/doku.php/download/mingw-builds).

3. Install the compiler. Sensible options for any modern (x64) machine are:
`x86_64`, `posix`, `seh`. I used the version `8.1.0` and build version `0`.
Use the default installation path; make sure to create a shortcut entry when
asked.

4. Using Windows explorer, go to `%ProgramFiles%\mingw-w64\`, most likely being
 `C:\Program Files\mingw-w64` on your computer. Open the folder in it. It would
 be something like `x86_64-8.1.0-posix-seh-rt_v6-rev0`. In there, run the
 `mingw-w64.bat` script.

5. A `Command Prompt` will open. Go to the folder where you have downloaded and
extracted the tarball. Basic `Command Prompt` navigation commands that you may
need are `cd <foldername>` (enter a folder), `dir` (list all files & folders)
and `cd ..` (go back to the parent folder).

6. Once inside the folder created after extracting the tarball, most likely
called `dftd3`, using the `dir` command will list a few files that end in `.f`,
a manual and a `Makefile`.

7. In this folder execute the following
```
gfortran -O -c dftd3.f -o dftd3.o
gfortran -O -c copyc6.f -o copyc6.o
gfortran -static dftd3.o copyc6.o -o dftd3 
```

8. You will find that new files have appeared in the folder. Now you can used
the file `dftd3` (it's an executable) as you would on a Linux system. More
details on how to use the command are in the manual (man.pdf).