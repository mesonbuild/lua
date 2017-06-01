src = [
  'lapi.c',
  'lcode.c',
  'lctype.c',
  'ldebug.c',
  'ldo.c',
  'ldump.c',
  'lfunc.c',
  'lgc.c',
  'llex.c',
  'lmem.c',
  'lobject.c',
  'lopcodes.c',
  'lparser.c',
  'lstate.c',
  'lstring.c',
  'ltable.c',
  'ltm.c',
  'lundump.c',
  'lvm.c',
  'lzio.c',
  'lauxlib.c',
  'lbaselib.c',
  'lbitlib.c',
  'lcorolib.c',
  'ldblib.c',
  'liolib.c',
  'lmathlib.c',
  'loslib.c',
  'lstrlib.c',
  'ltablib.c',
  'lutf8lib.c',
  'loadlib.c',
  'linit.c',
]

lualib = library('lua', src,
  dependencies : system_deps)

executable('luai', 'lua.c',
  link_with : lualib,
  dependencies : readline_dep)

# This only works with static linking.
if get_option('default_library') == 'static'
  executable('luac', 'luac.c',
    link_with : lualib)
endif
