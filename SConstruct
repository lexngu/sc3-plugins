# scons build script.
# blackrain at realizedsound dot net - 11 2006

# edit this to point to your SuperCollider3 source directory

sc3_source = '../supercollider'

##############################################
# simple ugens
headers = sc3_source + '/headers'

plugs = [
	'AmbisonicUGens',
	'BEQSuiteUGens',
	'BlackrainUGens',
	'JoshUGens',
	'ReverbUGens',
	'StkUGens'
]

for file in plugs :
	Environment(
        	CPPPATH = [headers + '/common', headers + '/plugin_interface', headers + '/server', 'source/StkUGens/include'],
        	CPPDEFINES = ['SC_LINUX', '_REENTRANT', 'NDEBUG', ('SC_MEMORY_ALIGNMENT', 1)],
        	CCFLAGS = ['-Wno-unknown-pragmas'],
        	CXXFLAGS = ['-Wno-deprecated -O3 '],
        	SHLIBPREFIX = '',
        	SHLIBSUFFIX = '.so'
	).SharedLibrary(file, 'source/' + file + '.cpp');

##############################################
# fft plugs

fft_src_base = [ sc3_source + '/source/plugins/fftlib.c', sc3_source + '/source/plugins/SCComplex.cpp',
	sc3_source + '/source/plugins/FFT2InterfaceTable.cpp', sc3_source + '/source/plugins/Convolution.cpp', 
	sc3_source + '/source/plugins/FeatureDetection.cpp' ]

Environment(
       	CPPPATH = [headers + '/common', headers + '/plugin_interface', headers + '/server', sc3_source + '/source/plugins'],
       	CPPDEFINES = ['SC_LINUX', '_REENTRANT', 'NDEBUG', ('SC_MEMORY_ALIGNMENT', 1)],
       	CCFLAGS = ['-Wno-unknown-pragmas'],
       	CXXFLAGS = ['-Wno-deprecated -O3 '],
       	SHLIBPREFIX = '',
       	SHLIBSUFFIX = '.so'
).SharedLibrary('JoshPVUGens', ['source/JoshPVUGens.cpp'] + fft_src_base);


