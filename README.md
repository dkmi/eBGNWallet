0. Prerequitites

Linux:

sudo apt-get install build-essential git cmake libboost1.55-all-dev
sudo apt-get install qtbase5-dev
Windows Dependencies: MSVC 2013 or later, CMake 2.8.6 or later, Boost 1.55, Qt 5.7. You may download them from: http://www.microsoft.com/ http://www.cmake.org/ http://www.boost.org/ https://www.qt.io/

1. Clone wallet sources

git clone https://github.com/dkmi/eBGNWallet.git
2 (Linux). Build

cp cryptonote/src/Platform/Posix/System/* cryptonote/src/System
mkdir build && cd build && cmake .. && make
**3 (OS X / macOS)

Install Xcode from AppStore

Install homebrew

Install dependencies:

brew install boost --c++11

brew install openssl - to install openssl headers

brew install pkgconfig

brew install cmake

brew install qt5 (or download QT 5.8+ from qt.io)

If you have an older version of Qt installed via homebrew, you can force it to use 5.x like so:

brew link --force --overwrite qt5

Add the Qt bin directory to your path

Example: export PATH=$PATH:$HOME/Qt/5.8/clang_64/bin

(Change this if our Qt version is newer than 5.8, example: export PATH=$PATH:$HOME/Qt/5.9/clang_64/bin)

This is the directory where Qt 5.x is installed on your system

Grab an up-to-date copy of the ebgn-wallet repository

git clone https://github.com/dkmi/ebgn-wallet.git

Go into the repository cd ebgn-wallet

Start the build: mkdir build && cd build && cmake .. && make

Make it static (to run on computers without Qt installed):

/usr/local/Cellar/qt/5.9.2/bin/macdeployqt ebgncoin.app

/path to macdeployqt may be different on your computer/

The executable can be found in the build folder.

Note: Workaround for "ERROR: Xcode not set up properly"

Edit $HOME/Qt/5.8/clang_64/mkspecs/features/mac/default_pre.prf

replace isEmpty($$list($$system("/usr/bin/xcrun -find xcrun 2>/dev/null")))

with isEmpty($$list($$system("/usr/bin/xcrun -find xcodebuild 2>/dev/null")))

More info: http://stackoverflow.com/a/35098040/1683164

4 (Windows). Build

cmake -G "Visual Studio 12" -DCMAKE_PREFIX_PATH=C:\Qt\5.8\msvc2013
This will create a engncoin.sln file which you can open in Visual Studio and build.

4 (Windows). Additional Files Required to run

For Windows, some QT files are also required. Copy the following from Qt to the eBGNCoin executable folder:

From C:\Qt\5.7\msvc2013\bin:

Qt5Core.dll
Qt5Gui.dll
Qt5Widgets.dll
From C:\Qt\5.7\msvc2013\plugins\platforms

platforms\qwindows.dll
If you are making a debug build you will need the altenatives to the above files which end in 'd', Like Qt5Coded.dll instead of Qt5Code.dll

The Folder structure should look like this:

Directory of C:\ebgncoin
         1,742,336 bgncoin.exe
        77,163,152 cryptonote.lib
        <DIR>          platforms
         4,673,536 Qt5Core.dll
         4,868,096 Qt5Gui.dll
         4,486,656 Qt5Widgets.dll

 Directory of C:\ebgncoin\platforms
           988,160 qwindows.dll
