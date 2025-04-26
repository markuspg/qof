libxml_req = '>= 2.5.10'

libxml_dep = dependency('libxml-2.0', version: libxml_req)

libqof_backend_qsf_deps = [
  glib_dep,
  libxml_dep,
]

libqof_backend_qsf_srcs = files(
  'qsf-backend.c',
  'qsf-xml.c',
  'qsf-xml-map.c',
)

library('libqof_backend_qsf',
  c_args: [
    '-DLOCALE_DIR="' + join_paths(get_option('prefix'), get_option('localedir')) + '"',
    '-DQSF_SCHEMA_DIR="' + join_paths(get_option('prefix'), get_option('datadir'), 'xml', 'qof', 'qsf') + '"',
    '-DQSF_SCHEMA_DIR="' + qsf_schema_dir + '"',
    '-D_XOPEN_SOURCE',
  ],
  dependencies: libqof_backend_qsf_deps,
  include_directories: [config_inc, libqof_inc],
  link_with: libqof,
  sources: libqof_backend_qsf_srcs,
)
