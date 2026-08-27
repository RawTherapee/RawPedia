---
aliases: ["/os_x/", "/osx/"]
title: "MacOS"
date: 2026-06-27
contributors:
  - DrSlony
  - Ion12
  - Ingo
  - Benitoite
  - Lebarhon
  - XavAL
tags:
  - 'Compiling'
toc: true
---

## How to compile RawTherapee on macOS

This page details instructions for compiling RawTherapee on macOS
systems. There are also separate pages with instructions for compiling
on [Linux](linux) and [Windows](windows). For more information regarding the cmake commands and dependencies, please refer to the 
[Linux](linux) article.

When in doubt, <big> ***[join us on the forum](forum)*** </big> and ask a human!

For instructions on cloning the source, choosing branches, configuring
CMake and doing the actual compilation, see these sections in the
[Linux](linux) guide. The information below is in addition to
that.

### Dependencies

See the list of dependencies in the [Compiling in Linux](linux#dependencies) article.
There are two separate package managers on macOS, [Homebrew](https://brew.sh), and MacPorts. Only use one package manager and configure the build for it:

#### Homebrew [🌐](https://brew.sh)

To install [Homebrew](https://brew.sh), use: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

The following command installs dependencies for RawTherapee:
`brew install imagemagick create-dmg libtiff gtk+3 gtkmm3 gtk-mac-integration adwaita-icon-theme libsigc++@2 little-cms2 libiptcdata fftw lensfun expat pkgconfig llvm shared-mime-info exiv2 jpeg-xl libomp automake libtool`

##### Configuring the homebrew build environment for Apple Silicon `arm64`

To your `cmake` command add the following flags:

```zsh
-DLOCAL_PREFIX:STRING="/opt/homebrew"
```

```zsh
-DCMAKE_OSX_ARCHITECTURES=arm64
```

#### MacPorts

Tested on OS X 10.9-12.

##### Prerequisites
  - Xcode Developer Tools & Command Line Tools
  - MacPorts
    - Detailed instructions on setting up MacPorts and the developer
      tools are available on the [MacPorts website](https://www.macports.org).
##### Configure MacPorts:


Add the following line to /opt/local/etc/macports/variants.conf

```zsh
+quartz -x11 -gnome +openmp
```
##### Installing dependencies

To install the dependencies, run from the terminal `sudo port install git cmake clang-11 libomp gtk3 gtkmm3 gtk-osx-application-gtk3 adwaita-icon-theme libsigcxx2 lcms2 libiptcdata fftw-3-single lensfun`

If compiling on Xcode 9.2 you will also need to do:

```zsh
sudo port install ld64 +ld64_xcode
```
#### Configuring compile system for MacPorts

To your `cmake` command add the following flag:

```zsh
-DLOCAL_PREFIX:STRING="/opt/local"
```

## Compiling

See the [Compiling in Linux](linux#compiling:_the_manual_way)
article for instructions on how to **clone** the source code, choose a
**branch** and how to configure **CMake**. Ignore the ***Now you are
ready to compile*** code on that page and follow the code on this page.

RawTherapee is compiled by the **clang** compiler. It may come with
XCode or be installed as a part of **llvm**. Be advised that Apple uses
a versioning scheme for **Apple clang** which is inconsistent with
**llvm clang**. To figure out which compiler to use, check your system
compiler first:

<small>

```zsh
% which clang
/usr/bin/clang

% /usr/bin/clang --version
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
```

</small>

If you see **`Apple clang`** mentioned in the top line of the `clang`
version output, note the version number it specifies and refer to
[this Wikipeda table](https://en.wikipedia.org/wiki/Xcode#Xcode_7.0_-_12.x_(since_Free_On-Device_Development))
for the mapping between **Apple clang** and **llvm clang** versions.
This knowledge may be useful when tracing any compilation errors.

If you want a generic \`x86_64\` build, use:

```zsh
-DPROC_TARGET_NUMBER="1"
```

and set the processor label manually by setting


```zsh
-DPROC_LABEL="generic processor"
```

If you want to compile a CPU-optimized build for your own computer's processor, use


```zsh
-DPROC_TARGET_NUMBER="2"
```

and then the processor label would be irrelevant, you could skip it.

To enable **SIMDE** accellerations on arm64 (apple silicon), add to your cmake command:

```zsh
-DWITH_SIMDE:BOOL=ON
```

### Deployment Target (Minimum macOS Version)

To set the deployment target, give the version number of the macos SDK you will be using:

```zsh
-DCMAKE_OSX_DEPLOYMENT_TARGET="26.1"
```

### Code Signature

To
[codesign](https://developer.apple.com/support/code-signing/) the
build, add your Apple "Developer ID Application" certificate name to the CMake command:

```zsh
-DCODESIGNID:STRING="Developer ID Application: Firstname Lastname (XXXXXXXXXX)"
```

The app and the generated dmg (Apple Disk Image) will be codesigned.

To sign ad-hoc (for your own machine), use `-` (a minus) as the Certificate name.

### App Notary

To
[notarize](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution/customizing_the_notarization_workflow?language=objc)
your codesigned build, include your app-specific notary credential in
the CMake command:

```zsh
-DNOTARY:STRING="--username user@mail.com --password abcd-efgh-ijkl-mnop"
```

The app and dmg will be notarized (scanned for malware) and stapled
(have the notarization ticket attached).

To build a universal app, enable it and provide the URL of the sister architechure's generated zip:

```zsh
-DOSX_UNIVERSAL:BOOL=ON \
-DOSX_UNIVERSAL_URL="file:///Volumes/Public/RawTherapee_macOS_x86_64_latest.zip"
```

To make a *Fancy* .dmg, enable it with:

```zsh
-DFANCY_DMG:BOOL=ON
```

### Compile RawTherapee

Now you are ready to compile:

```zsh
cd ~/repo-rt
rm -rf build
mkdir build && cd build
lensfun-update-data
cmake -DCMAKE_BUILD_TYPE="release" \
      -DPROC_TARGET_NUMBER="1" \
      -DPROC_LABEL="generic processor" \
      -DCACHE_NAME_SUFFIX="5-dev" \
      -DCMAKE_C_COMPILER="clang" \
      -DCMAKE_CXX_COMPILER="clang++" \
      -DWITH_LTO="OFF" \
      -DLENSFUNDBDIR="share/lensfun" \
      -DCMAKE_OSX_DEPLOYMENT_TARGET=10.15 \
      ..
make -j$(sysctl -n hw.ncpu) install
sudo make macosx_bundle
```

To compile RawTherapee with a specific llvm **clang** version (e.g.
installed via homebrew), use the following **cmake** command. When doing
so, make sure these settings point to the appropriate paths:

Using llvm 10 from homebrew:

```zsh
-DCMAKE_C_COMPILER="/usr/local/Cellar/llvm/10.0.1_1/bin/clang"
-DCMAKE_CXX_COMPILER="/usr/local/Cellar/llvm/10.0.1_1/bin/clang++"
-DCMAKE_AR="/usr/local/Cellar/llvm/10.0.1_1/bin/llvm-ar"
-DCMAKE_RANLIB="/usr/local/Cellar/llvm/10.0.1_1/bin/llvm-ranlib"
```

#### Example **`cmake`** command:

<div style="font-size: 12px;">

```zsh
cmake  .. \
    -DCMAKE_BUILD_TYPE="release" \
    -DPROC_TARGET_NUMBER="2" \
    -DCACHE_NAME_SUFFIX="5.8-dev" \
    -DCMAKE_C_COMPILER="/usr/local/Cellar/llvm/10.0.1_1/bin/clang" \
    -DCMAKE_CXX_COMPILER="/usr/local/Cellar/llvm/10.0.1_1/bin/clang++" \
    -DWITH_LTO="ON" \
    -DLENSFUNDBDIR="/Applications/RawTherapee.app/Contents/Resources/share/lensfun" \
    -DCMAKE_BUILD_TYPE=Release \
    -DOpenMP_C_FLAGS=-fopenmp=libomp \
    -DOpenMP_CXX_FLAGS=-fopenmp=libomp \
    -DOpenMP_C_LIB_NAMES="libomp" \
    -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_libomp_LIBRARY="/usr/local/lib/libomp.dylib" \
    -DOpenMP_CXX_FLAGS="-Wno-pass-failed -Wno-deprecated-register -Xpreprocessor -fopenmp /usr/local/lib/libomp.dylib -I/usr/local/include" \
    -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_C_FLAGS="-Wno-pass-failed -Wno-deprecated-register -Xpreprocessor -fopenmp /usr/local/lib/libomp.dylib -I/usr/local/include" \
    -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
    -DCMAKE_EXE_LINKER_FLAGS="-L/usr/local/opt/libffi/lib -L/usr/local/lib" \
    -DCMAKE_AR="/usr/local/Cellar/llvm/10.0.1_1/bin/llvm-ar" \
    -DCMAKE_RANLIB="/usr/local/Cellar/llvm/10.0.1_1/bin/llvm-ranlib" \
    -DCMAKE_OSX_DEPLOYMENT_TARGET=10.15
```

</div>

#### Example universal build on Apple Silicon using Homebrew, Apple Clang

<div style="font-size: 12px;">

```zsh
cd ~
git clone https://github.com/rawtherapee/rawtherapee repo-rt
cd repo-rt
mkdir build
cd build
date > stamp
date > message
cmake -DCMAKE_BUILD_TYPE="Release" \
    -DCMAKE_OSX_ARCHITECTURES=arm64 \
    -DPROC_TARGET_NUMBER="2" -DPROC_LABEL="arm64" \
    -DCACHE_NAME_SUFFIX="5-dev" -DCMAKE_C_COMPILER="clang" \
    -DCMAKE_CXX_COMPILER="clang++" \
    -DWITH_LTO="ON" \
    -DCMAKE_OSX_SYSROOT="/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    -DCMAKE_OSX_DEPLOYMENT_TARGET="26.1" -DLOCAL_PREFIX:STRING="/opt/homebrew" \
    -DLENSFUNDBDIR="/Applications/RawTherapee.app/Contents/Resources/share/lensfun" \
    -DCMAKE_EXE_LINKER_FLAGS="-Wl,-headerpad_max_install_names -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk -arch arm64" \
    -DOpenMP_C_FLAGS="-fopenmp=lomp" -DOpenMP_CXX_FLAGS=-fopenmp=lomp \
    -DOpenMP_C_LIB_NAMES="libomp" -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_libomp_LIBRARY="/opt/homebrew/opt/libomp/lib/libomp.dylib" \
    -DOpenMP_CXX_FLAGS="-Xpreprocessor -fopenmp /opt/homebrew/opt/libomp/lib/libomp.dylib -I/opt/homebrew/opt/libomp/include" \
    -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_C_FLAGS="-Xpreprocessor -fopenmp /opt/homebrew/opt/libomp/lib/libomp.dylib -I/opt/homebrew/opt/libomp/include" \
    -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
    -DWITH_SIMDE:BOOL=ON \
    -DOSX_UNIVERSAL_URL="file:///Volumes/Public/RawTherapee_macOS_x86_64_latest.zip" \
    -DOSX_UNIVERSAL:BOOL=ON \
    -DFANCY_DMG:BOOL=ON \
    -DCODESIGNID:STRING="$CODESIGN"  \
    -DNOTARY:STRING="$NOTARY" \
    ..
make -j8 install
sudo make macosx_bundle
```
</div>

<br>

###### From-Scratch Method used before High Sierra.

<details>

This [obsolete experimental script](https://raw.githubusercontent.com/Benitoite/RTdeps/master/macbuildRT.sh)
   script was helpful for dependency compilation.
  
A [JDK](https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html)
  must be installed.
  
Xcode 11.1+ [from Apple](https://developer.apple.com/xcode) must be installed
</details>

<hr>
<hr>

### Run and Share RawTherapee

You will find a disk image in the build directory; this is the
distribution release and can be run on any mac that matches the
architectures you compiled for.

For the release, Codesigning and Notarizing the app and dmg allows users to install and run RawTherapee under default system security settings.

The generated zip file is named according to this template:

<small> `RawTherapee_macOS_`*\<minimum supported macOS version\>*`_64_`*\<RawTherapee version\>*`.dmg.zip` </small>

For example: `RawTherapee_macOS_10.9_64_5.8-94-g4dbbc4053.dmg.zip`

Upload the zip archive to [file.io 🌐](http://file.io/) or your [iCloud](https://support.apple.com/guide/icloud/share-files-and-folders-mm708256356b/icloud) drive and
[open a new issue on our GitHub page](https://github.com/Beep6581/RawTherapee/issues/new)
with the link if you need help with your developement testing.

## Installing the RawTherapee Application on macOS

<div style="font-size: 32px; margin-left: 0em;">

To install the RawTherapee application, open the `.dmg` and drag the
RawTherapee app onto the `/Applications` folder.

To use the [command line interface (CLI)](command-line_options/#rawtherapee-cli), move
`rawtherapee-cli` into a folder in your \$PATH and install the RawTherapee
app as above.

</div>
