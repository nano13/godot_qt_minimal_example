# godot_qt_minimal_example
Trying to create a Godot Extension in C++ and with the use of Qt

The main issue I try to solve here is to bring together two different build-systems:
  * Godot is using SCons
  * Qt is using cmake or qmake

How do we create a solution to use Qt for a Godot-Extension?

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


