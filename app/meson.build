muse_framework_subproject = subproject('framework')

muse_global = muse_framework_subproject.target('muse_global')
muse_diagnostics = muse_framework_subproject.target('muse_diagnostics')
muse_languages = muse_framework_subproject.target('muse_languages')
muse_draw = muse_framework_subproject.target('muse_draw')
muse_ui = muse_framework_subproject.target('muse_ui')
muse_uicomponents = muse_framework_subproject.target('muse_uicomponents')
muse_dockwindow = muse_framework_subproject.target('muse_dockwindow')

better_inkscape_link = [
        lib_inkscape,
        muse_global,
        muse_languages,
        muse_draw,
        muse_uicomponents,
        muse_ui,
        muse_dockwindow
]

better_inkscape = executable('better-inkscape', 'main.cpp',
        link_with: better_inkscape_link)


