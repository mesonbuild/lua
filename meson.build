project('lua', 'c', version : '5.3.0', license : 'mit')

cc = meson.get_compiler('c')
m_dep = cc.find_library('m', required : false)

incdir = include_directories('src')
subdir('src')
