---
layout: post
title:  "How to install GDL on Ubuntu 22.04"
date:   2022-06-10 13:53:31 +0200
categories: mypost
---

## Introduction

Hi Everyone! Long time no see. :) I had this problem today, how to install GDL (or [GnuDataLanguage][GDL]) on Ubuntu 22.04 LTS. You can say of course, that you can use the standard

```bash
sudo apt install gnudatalanguage
```

but I meant how to compile it from source! For this, you'll need a working git and CMake (I prefer cmake-gui, but the real wizards of cmake rather use command line).

## How to obtain GDL source code

That is quite easy. You just need to type

```bash
git clone https://github.com/gnudatalanguage/gdl
```

Then you get the hard part, which packages to install to fully support all features of GDL?

For the basic support, you'll need to install the following packages.

```bash
sudo apt install binutils libopenmpi-dev mpi-default-bin libreadline-dev plplot-driver-xwin python3-dev libncurses-dev zlib1g-dev libgsl-dev libgraphicsmagick++1-dev libwxgtk3.0-gtk3-dev libnetcdf-dev libhdf4-dev libhdf5-dev fftw-dev libproj-dev shapelib libexpat1-dev mpi-default-dev libudunits2-dev libeigen3-dev libeccodes-dev libglpk-dev libplplot-dev libgeotiff-dev libfftw3-dev
```

There will be some additional packages added, just accept those as well.

Then open cmake-gui. Select the folder of the source code (for me it's home/my_user/gdl) and a build dir (for me it's home/my_user/gdl/build) and hit configure!

Then you get a pop-up window about the CMake Setup. The generator for me is Unix Makefiles and I hit "Use default native compilers", then Finish.

After configure, uncheck HDF in the list (you can use either netCDF or HDF4 but not both to my understanding at this time). And check MPI in the list (if it is not recognized automatically).

Then hit the Configure button again. Now in the list there should be everything ON, except:

1. GDLDEV mode
2. Xlib
3. HDF4 (or netCDF based on your decision)

Now hit the Generate button.

After it is successfully ran, close cmake-gui, navigate to your specified build directory and type:

```bash
make
```

Wait for make to finish and the navigate to the build/src folder and type:

```bash
./gdl
```

And now... GDL is ready to use! :)


[GDL]: https://github.com/gnudatalanguage/gdl
