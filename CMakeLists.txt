cmake_minimum_required(VERSION 3.0.0)
project(quickjs LANGUAGES C)

file(STRINGS VERSION version)

set(quickjs_src quickjs.c libbf.c libunicode.c libregexp.c cutils.c quickjs-libc.c)
set(quickjs_def CONFIG_VERSION="${version}" _GNU_SOURCE CONFIG_BIGNUM)


add_library(quickjs ${quickjs_src})
target_compile_definitions(quickjs PRIVATE ${quickjs_def} )

find_package(Threads)
target_link_libraries(quickjs ${CMAKE_DL_LIBS} m Threads::Threads)

