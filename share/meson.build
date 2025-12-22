# SPDX-License-Identifier: GPL-2.0-or-later

# Subdirectories for various components
subdir('attributes')
subdir('branding')
subdir('examples')
subdir('filters')
subdir('fonts')
subdir('icons')
subdir('keys')
subdir('markers')
subdir('paint')
subdir('palettes')
subdir('screens')
subdir('symbols')
subdir('templates')
subdir('tutorials')
subdir('ui')
subdir('doc')

# Define installation prefixes
inkscape_share_install = get_option('shareprefix')
extensions_dir = 'extensions'
themes_dir = 'themes'

# Install extensions directory
install_headers(extensions_dir, 
  install_dir: join_paths(inkscape_share_install, 'extensions'),
  exclude: ['.git*', '.pylintrc', '.darglint', '.pre-commit-config.yaml', 
             'tests', 'MANIFEST.in', 'pyproject.toml', 'Makefile', 
             '__pycache__', 'tox.ini', 'setup.cfg', 'requirements.txt', 
             'poetry.lock', '*.dox', '*.pyc', '*.sh', '*.bat', 
             '*.md', 'print_win32_vector.*', 'other/inkman'])

install_headers(join_paths(extensions_dir, 'other/inkman'), 
  install_dir: join_paths(inkscape_share_install, 'extensions', 'inkman'),
  exclude: ['tests', '.git*', 'MANIFEST.in', 'requirements.txt', 'pyproject.toml'])

# Windows specific installation
if host_machine.system() == 'windows'
  install_files(['${extensions_dir}/print_win32_vector.py', '${extensions_dir}/print_win32_vector.inx'], 
    install_dir: join_paths(inkscape_share_install, 'extensions'))

  message('Pre-compiling Python extensions to byte-code (.pyc files)')
  run_command(get_option('python'), '-m', 'compileall', '-qq', join_paths(inkscape_share_install))
endif()

# Install themes directory
install_headers(themes_dir, 
  install_dir: join_paths(inkscape_share_install, 'themes'),
  exclude: ['.git*', '*.md'])

# Application Desktop and AppData Files
if host_machine.system() == 'linux'
  if get_option('enable_binreloc')
    inkscape_iconpath = join_paths('${SNAP}', 'share', 'inkscape', 'branding', 'inkscape.svg')
  else
    inkscape_iconpath = 'org.inkscape.Inkscape'
  endif()

  inkscape_mimetype = [
    'image/svg+xml', 'image/svg+xml-compressed', 'application/vnd.corel-draw',
    'application/pdf', 'application/postscript', 'image/x-eps', 'application/illustrator',
    'image/x-wmf', 'image/x-emf', 'application/x-xccx', 'application/x-xcdt', 
    'application/x-xcmx', 'image/x-xcdr', 'application/visio', 'application/x-visio',
    'application/vnd.visio', 'application/vnd.ms-visio.viewer', 'application/visio.drawing',
    'application/vsd', 'application/x-vsd', 'image/x-vsd'
  ]

  foreach app : ['Inkscape', 'Inkview']
    desktop_template = join_paths(mesondir(), 'org.inkscape.' + app + '.desktop.template')
    desktop_file = join_paths(builddir(), 'org.inkscape.' + app + '.desktop.in')
    configure_file(input: desktop_template, output: desktop_file)
    
    if get_option('enable_nls')
      message('Generating desktop file for ' + app)
      configurable_file = join_paths(builddir(), 'org.inkscape.' + app + '.desktop')
      command = get_option('gettext_msgfmt_executable')
      run_command(command, '--desktop', '--template', desktop_file, '-d', join_paths(mesondir(), 'po'),
                  '-o', configurable_file, '--keyword=Name', '--keyword=GenericName',
                  '--keyword=X-GNOME-FullName', '--keyword=Comment', '--keyword=Keywords')

      install_headers(configurable_file, install_dir: join_paths(get_option('shareprefix'), 'applications'))
    else
      copy_files(desktop_file, join_paths(builddir(), 'org.inkscape.' + app + '.desktop'))
    endif
  endforeach()

  install_files(['${builddir}/org.inkscape.Inkscape.appdata.xml'], 
    install_dir: join_paths(get_option('shareprefix'), '