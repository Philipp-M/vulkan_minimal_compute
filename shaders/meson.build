shaders_src = ['shader.comp']

shaders = []
glslc = find_program('glslc')

foreach shader : shaders_src
	# get dependencies for each shader due to includes in glsl
	head_dep_shader = run_command(glslc, '-M', shader).stdout().strip().split(':')[1].split()
	header = custom_target(
		shader + '_spv',
		output: shader + '.spv.h',
		input: [shader] + head_dep_shader,
		command: [glslc, '-c', '-mfmt=c', '@INPUT0@', '-o', '@OUTPUT@'])
 	shaders += [header]
endforeach
