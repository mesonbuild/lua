src = ['lapi.c',
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
  lualib = shared_library('lua', src)
else
  lualib = static_library('lua', src)
endif

executable('luai', 'lua.c',
link_with : lualib)
executable('luac', 'luac.c',
link_with : lualib)
