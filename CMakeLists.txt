cmake_minimum_required(VERSION 3.0)
project(InsaneBump)

find_package(GTK2 REQUIRED)
include_directories(${GTK2_ATK_INCLUDE_DIR})
include_directories(${GTK2_CAIRO_INCLUDE_DIR})
include_directories(${GTK2_GDKCONFIG_INCLUDE_DIR})
include_directories(${GTK2_GDK_PIXBUF_INCLUDE_DIR})
include_directories(${GTK2_GLIBCONFIG_INCLUDE_DIR})
include_directories(${GTK2_GLIB_INCLUDE_DIR})
include_directories(${GTK2_GTK_INCLUDE_DIR})
include_directories(${GTK2_PANGO_INCLUDE_DIR})

find_path(LIBGIMP_INCLUDE_DIR libgimp PATH_SUFFIXES gimp-2.0)
find_library(LIBGIMP_LIBRARY NAMES gimp-2.0 libgimp-2.0 PATH_SUFFIXES lib)
find_library(LIBGIMP_UI_LIBRARY NAMES gimpui-2.0 libgimpui-2.0 PATH_SUFFIXES lib)
find_library(LIBGIMP_WIDGETS_LIBRARY NAMES gimpwidgets-2.0 libgimpwidgets-2.0 PATH_SUFFIXES lib)
include_directories(${LIBGIMP_INCLUDE_DIR})

include_directories(${CMAKE_SOURCE_DIR}/src)
include_directories(${CMAKE_SOURCE_DIR}/src/objects)
include_directories(${CMAKE_SOURCE_DIR}/src/win32c)

add_executable(gimp-plugin-insanebump
  src/InsaneBump.c
  src/interface.c
  src/main.c
  src/normalmap.c
  src/PluginConnectors.c
  src/preview_area.c
  src/scale.c)
target_link_libraries(gimp-plugin-insanebump
  m
  ${GTK2_GLIB_LIBRARY_RELEASE}
  ${GTK2_ATK_LIBRARY_RELEASE}
  ${GTK2_CAIRO_LIBRARY_RELEASE}
  ${GTK2_GDK_LIBRARY_RELEASE}
  ${GTK2_GDK_PIXBUF_LIBRARY_RELEASE}
  ${GTK2_GIO_LIBRARY_RELEASE}
  ${GTK2_GMODULE_LIBRARY_RELEASE}
  ${GTK2_GOBJECT_LIBRARY_RELEASE}
  ${GTK2_GTHREAD_LIBRARY_RELEASE}
  ${GTK2_GTK_LIBRARY_RELEASE}
  ${GTK2_PANGOCAIRO_LIBRARY_RELEASE}
  ${GTK2_PANGO_LIBRARY_RELEASE}
  ${LIBGIMP_LIBRARY}
  ${LIBGIMP_UI_LIBRARY}
  ${LIBGIMP_WIDGETS_LIBRARY})
# TODO: find gimp directory
install(TARGETS gimp-plugin-insanebump DESTINATION ~/.gimp-2.8/plug-ins)

