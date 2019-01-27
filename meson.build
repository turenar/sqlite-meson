project('sqlite', 'c', version : '3250100', license : 'pd')


thread_dep = dependency('threads')

cc = meson.get_compiler('c')
dl_dep = cc.find_library('dl', required: false)

c_args = []
if cc.has_header_symbol('unistd.h', 'usleep')
    # FIXME this is only for *nix cc, windows is not supported
    c_args += ['-DHAVE_USLEEP']
endif

sqinc = include_directories('.')
sqlib = library('sqlite', 'sqlite3.c', include_directories: sqinc,
    dependencies : [thread_dep, dl_dep],
    c_args: c_args)


sqlite_dep = declare_dependency(link_with : sqlib,
    include_directories : sqinc)
