---
title: How to convert raw formats to DNG
contributors:
  - Fherb
tags:
  - 'General Photography'
---

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Raw-Bilder zu DNG konvertieren

![](Adobe_dng_converter_83.png "Adobe_dng_converter_83.png") Digital
photography cameras can most often save your images in the
[JPEG](http://en.wikipedia.org/wiki/JPEG) format, as well as dump the
raw values from each of the millions of photosites which make up a
sensor and store them, along with some
[metadata](http://en.wikipedia.org/wiki/Metadata), in a proprietary
format. Some cameras also let you choose
[DNG](http://en.wikipedia.org/wiki/Digital_Negative) (Digital Negative)
as the raw format, which is a free and lossless format developed by
Adobe. Unlike JPEG images, which are already "developed", these raw
files (both proprietary and DNG) contain raw data (ergo the name "raw
file" - do not capitalize it, it is not an acronym!) which must first be
processed before an image is obtained.

There are numerous benefits in converting your raw files to the DNG
format:

1.  It has universal (or should I say "earthly"?) support. You may be
    able to use your DNG images in programs which do not have support
    for your non-DNG raw format.
2.  It is not a dead format - it is constantly maintained.
3.  Adobe's DNG Converter includes color matrices and white levels in
    the converted DNG files - these are usually not present in non-DNG
    files, and Adobe's ones are often more accurate than those from
    dcraw. This leads to more accurate color and lowers the chance of
    color casts in clipped areas.
4.  DNG files are often smaller than your original raw files due to
    better lossless compression.
5.  Even if your camera supports shooting straight to DNG, your camera's
    implementation of DNG is likely
    [outdated](https://en.wikipedia.org/wiki/Digital_Negative#Versions_of_the_specification).
    In some cases it may be warranted to re-convert your old DNGs to a
    newer DNG specification using the newest version of Adobe's DNG
    Converter. Possible reasons could be that the newer color matrices
    might be more accurate, lossless compression might be improved,
    improved support for defective pixel marking, inclusion of new
    opcodes, injection of new useful metadata tags, etc.

If you do convert your raw files to DNG, you should always first test
your DNG files to make sure everything in your workflow still functions
correctly before deleting the source files. Having said that, issues
with DNG are very rare, unlike the
[FUD](http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt)
surrounding it which is in no hurry of dying down.

Adobe's DNG Converter is not the only program that converts raw files to
DNG. There is, for example, the kipi-plugins DNG Image Converter which
uses [LibRaw](http://www.libraw.org/) and libkdcraw, however it is
unknown what matrices this converter uses or where it gets them from,
therefore it is safer if you stick to using the official Adobe DNG
Converter.

Get the latest version of Adobe DNG Converter here:

1.  [Adobe DNG Converter for
    Windows](http://www.adobe.com/support/downloads/product.jsp?product=106&platform=Windows)
    (get this if you're using Linux)
2.  [Adobe DNG Converter for Mac OS
    X](http://www.adobe.com/support/downloads/product.jsp?product=106&platform=Mac)

Run it and you're done.

## Unsupported sensors

![](Adobe_dng_converter_830.png "Adobe_dng_converter_830.png") Some
cameras have sensors with [color filter
array](https://en.wikipedia.org/wiki/Color_filter_array) layouts and
sensor pixel layouts unsupported by RawTherapee. Though you cannot
directly process these files in RawTherapee, you can convert them to a
supported demosaiced format using the Adobe DNG Converter. To do so, you
need to use the following settings:

- "Custom" compatibility mode using "DNG 1.4"
- "Linear (demosaiced)" must be ticked.

The resulting DNG files may end up being larger than the input files -
as an example, an input RAF file resulted in a DNG file 142% the size.

These demosaiced DNG files can now be used in RawTherapee (or any other
DNG-supporting program), though as they are already demosaiced the tools
in the "Raw" tab will be disabled.

Note that RawTherapee supports Fujifilm's X-Trans sensor type camera
models such as the X100S and X-Pro1 from version 4.2 onwards. Loading
these files in versions older than 4.2 will likely lead to a crash and
requires that you convert them to linear DNG as described above.

  

## Linux

Adobe DNG Converter is not designed for Linux, but it runs perfectly
fine through [wine](http://www.winehq.org/). Follow these steps:

1.  Install [wine](http://www.winehq.org/) (preferably using your
    package manager)
2.  Download [Adobe DNG Converter for
    Windows](http://www.adobe.com/support/downloads/product.jsp?product=106&platform=Windows)
3.  Install Adobe DNG Converter:
      
        WINEPREFIX="$HOME/wine-dng" wine /path/to/DNGConverter_version.exe

    It will install to
    "`$HOME/wine-dng/drive_c/Program Files (x86)/Adobe/Adobe DNG Converter.exe`"
4.  Run Adobe DNG Converter:
      
        WINEPREFIX="$HOME/wine-dng" wine "$HOME/wine-dng/drive_c/Program Files (x86)/Adobe/Adobe DNG Converter.exe"

    To make using it easier so you don't have to type all of this, make
    a shortcut to it:

        echo "alias dng='WINEPREFIX=\$HOME/wine-dng wine \"\$HOME/wine-dng/drive_c/Program Files (x86)/Adobe/Adobe DNG Converter.exe\"'" >> ~/.bashrc

    Now just restart your console and the shortcut works, so type "dng"
    and it starts. Magic!

You are done.

For your information - wine prefix  

When you run wine it will create a basic Windows system by default in
`$HOME/.wine`. That is called a "wine prefix". While it's fine to leave
it like that, you can run each Windows program in its own wine prefix,
so that you can easily and cleanly remove all traces of one program
without affecting the others. For example you might keep Adobe DNG
Converter in its own wine prefix in `$HOME/wine-dng` and decide to try
out some proprietary Windows HDR program. You might find out that you
don't like this program, or that the trial period has expired, or that
it simply doesn't work. Uninstalling it, if the uninstaller even works,
is known to leave things behind. If, on the other hand, you installed
this program to its own wine prefix, say `$HOME/wine-hdr`, you could
simply delete that folder and that program would be gone without a
trace, without affecting Adobe DNG Converter. Creating a new wine prefix
is very simple. All you have to do is to put
`WINEPREFIX=$HOME/some-folder` before the "`wine`" command. If that
folder does not exist, wine will create it for you. It is recommended
that you do not use hidden folders (ones with a period before the name,
like `$HOME/.wine`) for Windows programs, as some of them will not
display them. The above steps use a non-hidden custom wine prefix.
