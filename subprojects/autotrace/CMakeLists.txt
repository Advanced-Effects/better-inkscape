cmake_minimum_required(VERSION 3.12)

project(Autotrace LANGUAGES C)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GLIB REQUIRED glib-2.0)

set (autotrace_SRC
config.h
autotrace.c
autotrace.h
bitmap.c
bitmap.h
CMakeLists.txt
color.c
color.h
curve.c
curve.h
despeckle.c
despeckle.h
epsilon-equal.c
epsilon-equal.h
exception.c
exception.h
filename.c
filename.h
fit.c
fit.h
image-header.h
image-proc.c
image-proc.h
input.c
input.h
intl.h
logreport.c
logreport.h
median.c
module.c
output.c
output.h
private.h
pxl-outline.c
pxl-outline.h
quantize.h
spline.c
spline.h
thin-image.c
thin-image.h
types.h
vector.c
vector.h
xstd.h
)

add_library(autotrace_LIB ${autotrace_SRC})

target_include_directories(autotrace_LIB PRIVATE ${GLIB_INCLUDE_DIRS})
target_link_libraries(autotrace_LIB PRIVATE ${GLIB_LIBRARIES})
