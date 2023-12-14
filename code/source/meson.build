code = files('module.cpp')

lib = static_library('tscl-cpp',
    code,
    include_directories: dir)

tscl_cpp_dep = declare_dependency(
    link_with: lib,
    include_directories: dir)
