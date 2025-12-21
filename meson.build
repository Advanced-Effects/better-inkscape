# SPDX-License-Identifier: GPL-2.0-or-later

project('inkscape', 'cpp', 'c', version : '1.5.0-dev',
  default_options : [
    'cpp_std=c++20',
    'warning_level=3',
  ])

# TODO: Make this optional later
add_global_arguments('-D_AFXDLL=1', language: 'cpp')

# Define output directories
runtime_output_dir = ''.join([get_option('prefix'), 'bin'])
library_output_dir = ''.join([get_option('prefix'), 'lib'])
archive_output_dir = ''.join([get_option('prefix'), 'lib'])

# Dependent Libraries
dependency('boost', required : false)
dependency('gtest', required : false) # GTest

# Options
with_gnu_readline = get_option('with_gnu_readline')
enable_lcms = get_option('enable_lcms')
with_svg2 = get_option('with_svg2')
with_lpetool = get_option('with_lpetool')
lpe_enable_test_effects = get_option('lpe_enable_test_effects')
with_profiling = get_option('with_profiling')
build_shared_libs = get_option('build_shared_libs')
with_poppler = get_option('with_poppler')
with_capypdf = get_option('with_capypdf')
enable_poppler_cairo = get_option('enable_poppler_cairo')
with_image_magick = get_option('with_image_magick')
with_graphics_magick = get_option('with_graphics_magick')
with_libcdr = get_option('with_libcdr')
with_libvisio = get_option('with_libvisio')
with_libwpg = get_option('with_libwpg')
with_libspelling = get_option('with_libspelling')
with_gsourceview = get_option('with_gsourceview')
with_nls = get_option('with_nls')
with_jemalloc = get_option('with_jemalloc')
with_asan = get_option('with_asan')
with_internal_2geom = get_option('with_internal_2geom')
with_crossink = get_option('with_crossink')
with_fuzz = get_option('with_fuzz')
with_manpage_compression = get_option('with_manpage_compression')
enable_binary_relocation = get_option('enable_binary_relocation')

if build_shared_libs
  add_global_arguments('-fPIC', language: 'c')
endif

# Set install directories
install_dir = get_option('prefix')

# Subdirectories
subdir('src')
if with_nls
  subdir('po')
endif

if host_machine.system() != 'windows'
  subdir('man')
endif


# Summary

summary('Project name', meson.project_name())
summary('Project version', meson.project_version())
summary('Source dir:', meson.source_root())
summary('Binary dir:', meson.project_build_root())
summary('Install prefix:', install_dir)

summary('With GNU Readline', with_gnu_readline, section: 'Options')
summary('Enable LCMS', enable_lcms, section: 'Options')
summary('With SVG2', with_svg2, section: 'Options')
summary('With LPE tool', with_lpetool, section: 'Options')
summary('LPE: enable test effects', lpe_enable_test_effects, section: 'Options')
summary('With profiling', with_profiling, section: 'Options')
summary('Build shared libraries', build_shared_libs, section: 'Options')
summary('With Poppler', with_poppler, section: 'Options')
summary('With CapyPDF', with_capypdf, section: 'Options')
summary('Enable PopplerCairo', enable_poppler_cairo, section: 'Options')
summary('With ImageMagick', with_image_magick, section: 'Options')
summary('With GraphicsMagick', with_graphics_magick, section: 'Options')
summary('With LibCDR', with_libcdr, section: 'Options')
summary('With LibVISIO', with_libvisio, section: 'Options')
summary('With LibWPG', with_libwpg, section: 'Options')
summary('With LibSpelling', with_libspelling, section: 'Options')
summary('With GSourceView', with_gsourceview, section: 'Options')
summary('With NLS', with_nls, section: 'Options')
summary('With JeMalloc', with_jemalloc, section: 'Options')
summary('With ASAN', with_asan, section: 'Options')
summary('With internal 2GEOM', with_internal_2geom, section: 'Options')
summary('With Crossink', with_crossink, section: 'Options')
summary('With Fuzz', with_fuzz, section: 'Options')
summary('With manpage compression', with_manpage_compression, section: 'Options')
summary('Enable binary relocation', enable_binary_relocation, section: 'Options')