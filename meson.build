project('gslwasm', 'c',
    version : '0.0.0')

gsl_dep = dependency('gsl', method : 'pkg-config')

executable('newton',
    'rootnewton.c',
    dependencies : gsl_dep,
    name_suffix : 'js')

executable('integration',
    'integration.c',
    dependencies : gsl_dep,
    name_suffix : 'js')
