project('bitscript', 'c', 'cpp',
    license: 'MIT',
    version: '0.1.0',
    meson_version: '>= 0.54.1')

# Check compiler stuff
compiler = meson.get_compiler('c')

# Get all source information
bs_inc = include_directories('include')
subdir('lib')
subdir('tools')

# Setup Bitscript library
llvm_dep = dependency('LLVM', version : '>= 10.0', modules : ['core'])
bs_lib = library('bitscript', lib_src, dependencies: [llvm_dep], include_directories: bs_inc, install: true)
bs_dep = declare_dependency(include_directories: [bs_inc], link_with: [bs_lib], dependencies: [llvm_dep])

# Create bsc executable
bsc_exe = executable('bsc', bsc_src, dependencies: [bs_dep], install: true)
