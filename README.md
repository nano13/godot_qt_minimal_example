# godot_qt_minimal_example
Trying to create a Godot 4 Extension in C++ and with the use of Qt

The main issue I try to solve here is to bring together two different build-systems:
  * Godot is using SCons
  * Qt is using cmake or qmake

How do we create a solution to use Qt for a Godot-Extension?

## The Directory Structure of this Example Project
The Godot-Part is just the defaul tutorial for how to use GDExtension as explained in the Godot-Docs:
https://docs.godotengine.org/en/stable/tutorials/scripting/gdextension/gdextension_cpp_example.html

```
├── demo/ # contains the main Godot Project called main.gd and main.tscn
├── src/ # contains the source-files for our example Godot Extension
├── godot-cpp # contains our upstream Gotod-Repository as a git submodule
└── qt_minimal_example # contains a minimal qt example
```

* You can build the GDExtension-Example with the command `scons` as shown in `./compile.sh`
* You can build the Qt-Example with the command `cmake --build ../build-qtminex-Desktop-Debug --target all` as shown in `./qt_minimal_example/qtminex/compile.sh`

## The Goal: Utilizing Qt in the GDExtension Project
The file `./src/gdexample.h` contains in line 6 the commented out include line `//#include <QCoreApplication>`. If we comment that in, the SCons buildsystem used by Godot will not know how to handle that resulting in an error. If we try to compile this first with cmake/qmake, it will not be able to handle the Godot-Include `#include <godot_cpp/classes/sprite2d.hpp>` in line 4 also resulting in an error.

## Search Results
Even though I am not the first one trying to find a solution to e.g. use SCons for a Qt-Project, the search results are very rare and mostly severly outdated.

### lesser useful search results
  * Asked about ten years ago. Both Godot and Qt have evolved since quite a bit. Most links broken since (no surprise)
    * https://stackoverflow.com/questions/975188/how-do-i-use-qt-and-scons-together
  * Calls itself the 'Scons qt5 tool', but there is only one commit from five years ago, and the whole thing looks just like a bit of abandoned experimenting:
    * https://github.com/codytappan/SconsQt5
  * Pretty much this exact question asked in the Godot-Forums, but it is from 2017 and Godot has changed quite a bit since than. Also the Guy provides basically zero information of how he tried to solve the problem and how he actually managed to make it work:
    * https://ask.godotengine.org/17065/how-to-configure-godot-with-qt-using-scons-in-windows

### more promising search results
So the two basic ideas we could go down with are:
  * using cmake for godot (and Qt)
  * using scons for qt (and godot)

One question to be answered before would be what build system is better or more promising to begin with, and which of these approaches would make more sense / would be how much of an effort.

#### Using CMake for Godot
So far the most promising approach, but it is still going with GDNative (Godot 3.2.3), which is the predecessor of Godot 4's GDExtension:
  * https://thatonegamedev.com/cpp/godot-native-using-cmake/

#### Using SCons for Qt
  * https://github.com/SCons/scons/wiki/FromQmakeToScons?highlight=(qt)

