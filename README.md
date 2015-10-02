GIMP Plug-In InsaneBump
=======================

Gimp plug-in for normal map generation.

* Copyright (C) 2013 Omar Emad
* Copyright (C) 2013 Derby Russell

Features
========

* Automake/Autoconf was replaced with CMake.

Requirements
============

* libgimp2.0-dev

Installation
============

Change installation directory in CMakeLists.txt:
```
install(TARGETS gimp-plugin-insanebump DESTINATION ~/.gimp-2.8/plug-ins)
```

Build and install plug-in:
```
$ cmake .
$ make install
```

