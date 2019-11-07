lex_exe = find_program('flex', required: true)
bison_exe = find_program('bison', required: true)

lgen = generator(lex_exe, output: '@PLAINNAME@.yy.c', arguments: ['-o', '@OUTPUT@', '@INPUT@'])
pgen = generator(bison_exe,
	output: ['@BASENAME@.tab.c', '@BASENAME@.tab.h'],
	arguments: ['@INPUT@', '--defines=@OUTPUT1@', '--output=@OUTPUT0@']
)

sources = files(
	'asm.c'
)

lexfiles = lgen.process('lexer.l')
parsefiles = pgen.process('parser.y')

asm_lib = library(meson.project_name(), sources, lexfiles, parsefiles, install:true)
asm_inc = include_directories('.')

asm_dep = declare_dependency(link_with: asm_lib, include_directories: asm_inc)

asm_exe = executable(meson.project_name(), 'main.c', lexfiles, parsefiles, link_with: asm_lib, install:true)

install_headers('asm.h', subdir: 'evasm')
