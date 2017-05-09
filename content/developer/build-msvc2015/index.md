---
title: Build QuantumPT
prev: /developer/architecture
next: /release
weight: 60
toc: true
---

{{% notice tip %}}
This page shows you how to build `QuantumPT` application from scratch on Windows 7 using `pyqtdeploy`.
{{% /notice %}}

## Requirements

{{% notice note %}}
ALL packages need to be installed for 32-bits, it will work even if you have a 64-bits system.
{{% /notice %}}

* Windows 7 (x64 or x86)
* [Python 3.6.x](https://www.python.org/ftp/python/3.6.1/python-3.6.1.exe) (any version should do it, e.g 3.6.1)
* [Qt 5.8.0 for Windows 32-bit (VS 2015, 1.0 GB)](http://download.qt.io/archive/qt/5.8/5.8.0/qt-opensource-windows-x86-msvc2015-5.8.0.exe)
* [Microsoft Visual Studio 2015 Community Edition](https://github.com/QuantumPrayerTimes/documentation/files/985580/vs_community_ENU_2015.gz)
* [sip 4.19.2 (source)](https://sourceforge.net/projects/pyqt/files/sip/sip-4.19.2/sip-4.19.2.zip)
* [PyQt 5.8.2 (source)](https://sourceforge.net/projects/pyqt/files/PyQt5/PyQt-5.8.2/PyQt5_gpl-5.8.2.zip)

{{% notice info %}}
Make sure that the `Qt`, `PyQt5`, `Python` and `Microsoft Visual Studio` version match.
This guide supposes you do not have a previous version of softwares installed.
{{% /notice %}}

## Installation

### Python 3.6.x

The installation of `Python` is straight forward however you will need some modification to make task easier.

* Check **Add Python 3.6 to PATH** and modify the installation to path `C:\Python36\` 
<table border="0">
    <tr>
        <td align="center" valign="center">
            <p>Add Python 3.6 to PATH</p>
            <img src="https://cloud.githubusercontent.com/assets/9877335/25791123/fd6bd334-3372-11e7-8fdf-9b94b8c8f622.png"/>
        </td>
        <td align="center" valign="center">
            <p>Modify the installation to path</p>
            <img src="https://cloud.githubusercontent.com/assets/9877335/25791122/fd6a8574-3372-11e7-9721-1851dd9bd66d.png"/>
        </td>
    </tr>
</table>

You will also need to install `Python` packages :

{{% notice info %}}
Before continuing the tutorial, make sure you are using Python 3.6.x version of python.
To verify, run `python` command in a terminal and read the output, it should print the used Python version.
{{% /notice %}}

```bash
python -m pip install "APScheduler>=3.3.1" "geoip2>=2.4.2" "pytz>=2017.2" "requests>=2.13.0" "PyQt5>=5.8.2" "appdirs>=1.4.3" "packaging>=16.8" "pyparsing>=2.2.0" "pyqtdeploy>=1.3.2"
```

### Qt 5.8.0

The installation of `Qt` is straight forward and does not need any particular settings (use the default settings *unless you know what you are doing*).

* Make sure to install Qt in the `C:\Qt\Qt5.8.0\` directory. This should be the default path.

### Microsoft Visual Studio 2015

The installation of `Microsoft Visual Studio 2015` is a little bit different and needs more configuration.

`Common Tools C++ for Visual C++ 2015` feature needs to be enabled in order to compile correctly `PyQt` applications.

When running the installer, make sure the feature is enabled :

<table border="0">
    <tr>
        <td align="center" valign="center">
            <img src="https://cloud.githubusercontent.com/assets/9877335/25792905/50981cb0-337e-11e7-9593-88fcf0315a2c.png"/>
        </td>
        <td align="center" valign="center">
            <img src="https://cloud.githubusercontent.com/assets/9877335/25792906/50ab6a54-337e-11e7-8d4b-a5286e334cdd.png"/>
        </td>
    </tr>
</table>

## Compilation

In order to build QuantumPT, we need to compile `PyQt5` and `sip` from sources.

After downloading sources from requirements, extract the archives in the same directory (easy for compilation)

Let's create an environment to compile PyQt and SIP (**in order to compile PyQt, we need first to compile sip**)

* Create a folder "compilation" in your Desktop (for example)
* Extract the content of your sip archive in this forlder
* Extract the content of your PyQt5 archive in this forlder

You should have now :

```bash
.
└── compilation
    ├── sip-4.19.2/
    └── PyQt5_gpl-5.8.2/
```

### [Compilation] sip

* Open a terminal
* Navigate to `sip-4.19.2` directory
* Run :

```bash
python configure.py
```

At this step, you did not install `sip`, you only configured it (basically its installation dir, etc...)

* **VERY IMPORTANT STEP** source your environment variables by running in the terminal :

```bash
# Keep the double quotes (Windows does not like spaces)
"C:\Qt\Qt5.8.0\5.8\msvc2015\bin\qtenv2.bat"
```

After running this command, it automatically change your current directory.

* **Stay on the terminal** and re-navigate to your `sip-4.19.2` directory and run:

```bash
# Keep the double quotes (Windows does not like spaces)
"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"
```

* **(always in the same terminal)** run :

```bash
nmake
```

* Finally, run :

```bash
nmake install
```

### [Compilation] PyQt5

The steps are almost the same as sip but it will take more time.

* Open a terminal
* Navigate to `PyQt5_gpl-5.8.2` directory
* Run :

```bash
python configure.py --disable QtNfc --confirm-license
```

Note that this command disable QtNfs because of a compilation problem we could not resolve. It will also automatically accepts the license.

* **VERY IMPORTANT STEP** source your environment variables by running in the terminal :

```bash
# Keep the double quotes (Windows does not like spaces)
"C:\Qt\Qt5.8.0\5.8\msvc2015\bin\qtenv2.bat"
```

After running this command, it automatically change your current directory.

* **Stay on the terminal** and re-navigate to your `PyQt5_gpl-5.8.2` directory and run:

```bash
# Keep the double quotes (Windows does not like spaces)
"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"
```

* **(always in the same terminal)** run :

```bash
nmake
```

{{% notice warning %}}
Notice that we did not run the `nmake install` command for PyQt5, if you run the command, it will install the libraries 
in `C:\Python36` site-packages and replaces the `PyQt5` installed by `pip` so `PyQt5` modules will be broken.
{{% /notice %}}

## Build

* Open a terminal
* Clone the `QuantumPT` repository in a specific folder

```bash
git clone https://github.com/QuantumPrayerTimes/quantumpt.git 
```

* **VERY IMPORTANT STEP** source your environment variables by running in the terminal :

```bash
# Keep the double quotes (Windows does not like spaces)
"C:\Qt\Qt5.8.0\5.8\msvc2015\bin\qtenv2.bat"
```

After running this command, it automatically change your current directory.

* **Stay on the terminal** and navigate to your `QuantumPT` directory that you cloned and run:

```bash
# Keep the double quotes (Windows does not like spaces)
"C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"
```

* **(always in the same terminal)** run :

```bash
pyqtdeploy build.pdy
```

* The `pyqtdeploy` application will open, navigate to the latest tab `Build`, check `Run qmake` and `Run make`
* Build the application by clicking on the `Build` button

![2017-05-07_23-36-12](https://cloud.githubusercontent.com/assets/9877335/25792843/fad28ed2-337d-11e7-8aa1-52f3367cdecd.png)

The output will be located in `QuantumPT` directory under `build/release/`

## Packaging

{{% notice note %}}
We will need to get some files now because the executable generated is not complete, it needs to be linked to some
libraries.
{{% /notice %}}

* Create a `custom-release` directory that will contain the builded release

* In the `build/release/` directory, copy the `QuantumPT.exe` binary to `custom-release` directory

* Navigate to `sip-4.19.2` directory

* Copy the following `sip` library to `custom-release` directory

```bash
sip-4.19.2\siplib\sip.pyd
```

* Navigate to `PyQt5_gpl-5.8.2` directory

* Copy the following `Qt` libraries to `custom-release` directory

```bash
PyQt5_gpl-5.8.2\Qt\release\Qt.dll
PyQt5_gpl-5.8.2\QtCore\release\QtCore.dll
PyQt5_gpl-5.8.2\QtGui\release\QtGui.dll
PyQt5_gpl-5.8.2\QtWidgets\release\QtWidgets.dll
PyQt5_gpl-5.8.2\QtMultimedia\release\QtMultimedia.dll
PyQt5_gpl-5.8.2\QtNetwork\release\QtNetwork.dll
PyQt5_gpl-5.8.2\QtSql\release\QtSql.dll
```

* Navigate to `C:\Python36` directory

* Copy the following `Python` system libraries to `custom-release` directory

```bash
C:\Python36\python3.dll
C:\Python36\python36.dll
```

* Copy the following `Python` libraries to `custom-release\lib` directory

```bash
C:\Python36\DLLs\_multiprocessing.pyd
C:\Python36\DLLs\_socket.pyd
C:\Python36\DLLs\pyexpat.pyd
C:\Python36\DLLs\select.pyd
C:\Python36\DLLs\unicodedata.pyd
```

* Navigate to `C:\Qt\Qt5.8.0` directory 

* Copy the following `Qt` libraries to `custom-release` directory

```bash
C:\Qt\Qt5.8.0\5.8\msvc2015\bin\Qt5Core.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\bin\Qt5Gui.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\bin\Qt5Widgets.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\bin\Qt5Multimedia.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\bin\Qt5Network.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\bin\Qt5Sql.dll
```

* Copy the following `Qt` plugins to `custom-release` directory keeping the folders architecture

```bash
C:\Qt\Qt5.8.0\5.8\msvc2015\plugins\platforms\qwindows.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\plugins\mediaservice\dsengine.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\plugins\mediaservice\qtmedia_audioengine.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\plugins\mediaservice\wmfengine.dll
C:\Qt\Qt5.8.0\5.8\msvc2015\plugins\sqldrivers\qsqlite.dll
```

* Navigate to `QuantumPT` directory

* Copy the following resources to `custom-release` directory keeping the folders architecture

```bash
resources\database\database.db
resources\database\ip_location.mmdb
resources\multimedia\athans\*
resources\multimedia\duas\*
```

* Navigate to `Microsoft Visual Studio 2015` directory

* Copy the following `Microsoft Visual Studio 2015` libraries to `custom-release` directory

```bash
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\redist\x86\Microsoft.VC140.CRT\msvcp140.dll
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\redist\x86\Microsoft.VC140.CRT\vcruntime140.dll
```

{{% notice tip %}}
Finally, the build is complete and a new release has been generated.
{{% /notice %}}

The release architecture should looks like the following :

```bash
.
├── lib
|   ├── _multiprocessing.pyd
|   ├── _socket.pyd
|   ├── pyexpat.pyd
|   ├── select.pyd
|   └── unicodedata.pyd
├── plugins
|   ├── mediaservice
|   |   ├── dsengine.dll
|   |   ├── qtmedia_audioengine.dll
|   |   └── wmfengine.dll
|   ├── platforms
|   |   └── qwindows.dll
|   └── sqldrivers
|       └── qsqlite.dll
├── resources
|   ├── database
|   |   ├── database.db
|   |   └── ip_location.mmdb
|   └── multimedia
|       ├── athans
|       |   ├── athan_1.mp3
|       |   └── [...]
|       └── duas
|           ├── doua_001.mp3
|           └── [...]
├── msvcp140.dll
├── python3.dll
├── python36.dll
├── Qt.dll
├── Qt5Core.dll
├── Qt5Gui.dll
├── Qt5Multimedia.dll
├── Qt5Network.dll
├── Qt5Sql.dll
├── Qt5Widgets.dll
├── QtCore.dll
├── QtGui.dll
├── QtMultimedia.dll
├── QtNetwork.dll
├── QtSql.dll
├── QtWidgets.dll
├── QuantumPT.exe
├── vcruntime140.dll
└── sip.pyd
```

