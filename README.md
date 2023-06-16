# godot_qt_minimal_example
Trying to create a Godot Extension in C++ and with the use of Qt

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

## Utilizing Qt in the GDExtension Project
The file `./src/gdexample.h` contains in line 6 the commented out include line `//#include <QCoreApplication>`. If we comment that in, the SCons buildsystem used by Godot will not know how to handle that resulting in an error. If we try to compile this first with cmake/qmake, it will not be able to handle the Godot-Include `#include <godot_cpp/classes/sprite2d.hpp>` also resulting in an error.

## Search Results
Even though I am not the first one trying to find a solution to e.g. use SCons for a Qt-Project, the search results are very rare and mostly severly outdated.

Here are a few examples:
  * https://stackoverflow.com/questions/975188/how-do-i-use-qt-and-scons-together
  * https://github.com/codytappan/SconsQt5
  * https://ask.godotengine.org/17065/how-to-configure-godot-with-qt-using-scons-in-windows
