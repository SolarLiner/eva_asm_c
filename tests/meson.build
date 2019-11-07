test_dep = subproject('evatest').get_variable('test_dep')

tests = [['tests', 'test.c']]

foreach test : tests
	exe = executable(test[0], test[1], dependencies:test_dep)
	test(test[0], exe)
endforeach
