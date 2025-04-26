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
package = meson.project_name()
soname = qof_current

glib_req = '>= 2.9.0'

glib_dep = dependency('glib-2.0', version: glib_req)
gmodule_dep = dependency('gmodule-2.0', version: glib_req)
gobject_dep = dependency('gobject-2.0', version: glib_req)

conf_data = configuration_data()
conf_data.set_quoted('GETTEXT_PACKAGE', meson.project_name())
conf_data.set_quoted('PACKAGE', meson.project_name())
configure_file(
  configuration: conf_data,
  output: 'config.h',
)

config_inc = include_directories('.')

subdir('lib')
subdir('qof')
subdir('backend')
