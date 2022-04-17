project('gslwasm', 'c',
    version : '0.0.0')

inc = include_directories('include')

cc = meson.get_compiler('c')
gsl = declare_dependency(
    dependencies : cc.find_library('gsl', dirs : meson.current_source_dir()),
    version : '2.7.1',
    include_directories : inc
)

executable('newton',
    'rootnewton.c',
    include_directories : inc,
    dependencies : gsl,
    name_suffix : 'js')
