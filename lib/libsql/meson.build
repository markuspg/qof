lex = find_program('lex', 'flex')
yacc = find_program('yacc', 'bison')

parser_c = custom_target('parser_c',
  build_by_default: true,
  command: [yacc, '-v', '-d', '-o', '@OUTPUT@', '-p', 'sql', '@INPUT@'],
  input: 'parser.y',
  output: 'parser.c',
)

lexer_c = custom_target('lexer_c',
  build_by_default: true,
  command: [lex, '-o@OUTPUT@', '-Psql', '@INPUT@'],
  depends: parser_c,
  input: 'lexer.l',
  output: 'lexer.c',
)

libqofsql_deps = [
  glib_dep,
]

libqofsql_headers = files(
  'sql_parser.h',
)
install_headers(libqofsql_headers)

libqofsql_srcs = files(
  'mem.c',
  'sql_display.c',
  'sql_parser.c',
  'sql_tree.c',
)
libqofsql_srcs += [
  lexer_c,
  parser_c,
]

libqofsql = library('libqofsql',
  dependencies: libqofsql_deps,
  # link_args: ['-version-info "' + lib_sql_vers + '"' ],
  sources: libqofsql_srcs,
)

libqofsql_inc = include_directories('.')

sql_parse_test_deps = [
  glib_dep,
]

sql_parse_test_srcs = files(
  'sql_parse_test.c',
)

executable('sql_parse_test',
  build_by_default: false,
  dependencies: sql_parse_test_deps,
  link_with: libqofsql,
  sources: sql_parse_test_srcs,
)
