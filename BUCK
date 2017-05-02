include_defs('//BUCKAROO_DEPS')

mono_sources = [
  'src/autofit/autofit.c',
  'src/bdf/bdf.c',
  'src/cache/ftcache.c',
  'src/cff/cff.c',
  'src/pcf/pcf.c',
  'src/pfr/pfr.c',
  'src/psaux/psaux.c',
  'src/pshinter/pshinter.c',
  'src/psname/psname.c',
  'src/raster/raster.c',
  'src/sfnt/sfnt.c',
  'src/smooth/smooth.c'
]

macos_sources = glob([
  'src/base/ftmac.c',
])

linux_sources = glob([

])

windows_sources = glob([

])

platform_sources = macos_sources + windows_sources + linux_sources

cxx_library(
  name = 'freetype2',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('include', '**/*.h'),
  ]),
  headers = subdir_glob([
    ('src', '**/*.h'),
  ]),
  srcs = glob([
    'src/**/*.c',
  ],
  excludes = glob([
    'src/autofit/aflatin2.c',
    'src/gzip/infutil.c',
  ]) + platform_sources + mono_sources),
  platform_srcs = [
    ('default', linux_sources),
    ('^linux.*', linux_sources),
    ('^macos.*', macos_sources),
    ('^windows.*', windows_sources),
  ],
  compiler_flags = [
    '-std=c11',
    '-DFT2_BUILD_LIBRARY',
    '-DFT_ADVANCES_H=<freetype/ftadvanc.h>',
    '-DFT_INTERNAL_DEBUG_H=<freetype/internal/ftdebug.h>',
    '-DFT_INTERNAL_DRIVER_H=<freetype/internal/ftdriver.h>',
    '-DFT_INTERNAL_MEMORY_H=<freetype/internal/ftmemory.h>',
    '-DFT_INTERNAL_OBJECTS_H=<freetype/internal/ftobjs.h>',
    '-DFT_INTERNAL_POSTSCRIPT_AUX_H=<freetype/internal/psaux.h>',
    '-DFT_INTERNAL_STREAM_H=<freetype/internal/ftstream.h>',
    '-DFT_SERVICE_POSTSCRIPT_CMAPS_H=<freetype/internal/services/svpscmap.h>',
    '-DFT_CONFIG_OPTION_SYSTEM_ZLIB',
  ],
  visibility = [
    'PUBLIC',
  ],
  deps = BUCKAROO_DEPS,
)
