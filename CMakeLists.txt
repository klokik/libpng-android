# cmake_minimum_required(VERSION 2.6)

# project(libpng C)
set(MODULE_NAME png_internal)

find_package(ZLIB REQUIRED)
include_directories(${ZLIB_INCLUDE_DIR})

set(SRCS
	src/png.c
	src/pngerror.c
	src/pngget.c
	src/pngmem.c
	src/pngpread.c
	src/pngread.c
	src/pngrio.c
	src/pngrtran.c
	src/pngrutil.c
	src/pngset.c
	src/pngtrans.c
	src/pngwio.c
	src/pngwrite.c
	src/pngwtran.c
	src/pngwutil.c
)

# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

add_library(${MODULE_NAME} STATIC ${SRCS})
target_link_libraries(${MODULE_NAME} ${ZLIB_LIBRARY})

set(ADDITIONAL_LIBRARIES ${ADDITIONAL_LIBRARIES} ${MODULE_NAME} CACHE INTERNAL "")