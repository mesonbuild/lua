project(
  'lua', 'c',
  license: 'MIT',
  meson_version: '>=0.50.1',
  version: '5.1.5',
)

project_options = ['warning_level=1', 'c_std=c99']
cc = meson.get_compiler('c')

# Get rid of warnings, at least on clang and gcc.
if cc.get_id() == 'gcc'
  add_project_arguments(
    '-Wno-misleading-indentation',
    language: 'c',
  )
elif cc.get_id() == 'clang'
  add_project_arguments(
    '-Wno-empty-body',
    '-Wno-misleading-indentation',
    language: 'c',
  )
endif

os = host_machine.system()
if os == 'darwin'
  add_project_arguments('-DLUA_USE_MACOSX', language: 'c')
elif os != 'windows' and os != 'emscripten'
  add_project_arguments('-DLUA_USE_POSIX', language: 'c')
  if os == 'linux'
    add_project_arguments('-D_DEFAULT_SOURCE', language: 'c')
  endif
endif

lua_lib_deps = [cc.find_library('m', required: false)]

dl_dep = cc.find_library('dl', required: get_option('use_dlopen'))
if dl_dep.found()
  lua_lib_deps += [dl_dep]
  add_project_arguments('-DLUA_USE_DLOPEN', language: 'c')
endif

subdir('src')

lua_versions = meson.project_version().split('.')

lua_lib = library('lua',
  lualib_src,
  dependencies: lua_lib_deps,
  override_options: project_options,
  version: meson.project_version(),
  # soversion of 5.1. Otherwise, it would be just 5 which wouldn't work since Lua isn't
  # compatible over minor versions.
  soversion: lua_versions[0] + '.' + lua_versions[1],
  implicit_include_directories: false,
)

lua_exe = executable('lua',
  luaexe_src,
  link_with: lua_lib,
  export_dynamic: dl_dep.found(),
  override_options: project_options,
  implicit_include_directories: false,
)

if get_option('default_library') == 'static'
  luac_exe = executable('luac',
    luacexe_src,
    link_with: lua_lib,
    override_options: project_options,
    implicit_include_directories: false,
  )
endif

lua_dep = declare_dependency(link_with: lua_lib, include_directories: 'src')
