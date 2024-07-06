project('tox-meson-example',
  ['c', 'fortran'],
  version : '0.1',
  meson_version: '>= 1.1.0',
  default_options : [
    'warning_level=1',
    'buildtype=release'
  ])

py = import('python').find_installation(pure: false)
py_dep = py.dependency()

incdir_numpy = run_command(py,
  ['-c', 'import numpy; print(numpy.get_include())'],
  check : true
).stdout().strip()

incdir_f2py = run_command(py,
    ['-c', 'import numpy.f2py; print(numpy.f2py.get_include())'],
    check : true
).stdout().strip()

fortranobject_c = incdir_f2py / 'fortranobject.c'

inc_np_all = include_directories(incdir_numpy, incdir_f2py)
