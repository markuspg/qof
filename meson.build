project('qof',
  'c',
  default_options : [
    'c_std=gnu99',
  ],
  license: 'GPL-2.0-or-later',
  meson_version: '>= 0.49',
  version: '0.8.9',
)

qof_current = '2'

sql_current = '1'
sql_revision = '2'
sql_age = '0'
lib_sql_vers = sql_current + ':' + sql_revision + ':' + sql_age

soname = qof_current

package = meson.project_name()

glib_req = '>= 2.9.0'

glib_dep = dependency('glib-2.0', version: glib_req)
gmodule_dep = dependency('gmodule-2.0', version: glib_req)
gobject_dep = dependency('gobject-2.0', version: glib_req)

qsf_schema_dir = join_paths(get_option('datadir'), 'xml', 'qof', 'qsf')

conf_data = configuration_data()
conf_data.set_quoted('GETTEXT_PACKAGE', meson.project_name())
conf_data.set_quoted('QOF_LIB_DIR', join_paths(get_option('libdir'), meson.project_name() + soname))
conf_data.set_quoted('LOCALE_DIR', get_option('localedir'))
conf_data.set_quoted('PACKAGE', meson.project_name())
conf_data.set_quoted('QOF_LIB_DIR', join_paths(get_option('libdir'), meson.project_name() + soname))
configure_file(
  configuration: conf_data,
  output: 'config.h',
)

config_inc = include_directories('.')

subdir('lib')
subdir('qof')
subdir('backend')
