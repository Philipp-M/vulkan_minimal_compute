project('vulkan_minimal_compute', 'cpp',
  license: 'MIT',
  version: '0.1.0',
  meson_version: '>=0.42',
  default_options: ['cpp_std=c++17'])

## default arrguments
## warnings and stuff
add_project_arguments(
  '-Wall',
  '-Wextra',
  '-Wno-unused-parameter',
  '-Wpedantic',
  '-Wno-missing-braces',
  language: 'cpp')

# project-specific stuff
source_root = meson.source_root().split('\\')
add_project_arguments('-DDLG_BASE_PATH="' + '/'.join(source_root) + '/"', language: 'cpp')

dep_vulkan = dependency('vulkan')

## shader compilation

subdir('shaders')
shader_inc = include_directories('shaders') # for headers in build folder

src = [ 'src/main.cpp',
        'src/lodepng.cpp',
        shaders
      ]

executable('vulkan_minimal_compute', src, dependencies: [dep_vulkan], include_directories: shader_inc)
