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
        
if get_option('shared_lib')
  libtype = 'shared_library'
else
  libtype = 'static_library'
endif

lualib = build_target('lua', src,
  target_type : libtype,
  dependencies : libm)

luai = executable('luai', 'lua.c',
  link_with : lualib)
luac = executable('luac', 'luac.c',
  link_with : lualib)

test('luahello', luai, args : ['-e', 'print("hello")'])
