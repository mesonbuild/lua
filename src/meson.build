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

# LuaC requires a static library
lualib_link = static_library('lua', src,
  dependencies : m_dep)

lualib = library('lua', src)

luai = executable('luai', 'lua.c',
  link_with : lualib_link,
  dependencies : m_dep)
luac = executable('luac', 'luac.c',
  link_with : lualib_link,
  dependencies : m_dep)

test('luahello', luai, args : ['-e', 'print("hello")'])