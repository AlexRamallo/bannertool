cmake_minimum_required(VERSION 3.0.0 FATAL_ERROR)
project(bannertool VERSION 1.2.0 LANGUAGES CXX C)

set(SOURCES
	${CMAKE_SOURCE_DIR}/source/main.cpp
	${CMAKE_SOURCE_DIR}/source/cmd.cpp

	${CMAKE_SOURCE_DIR}/source/pc/stb_image.c
	${CMAKE_SOURCE_DIR}/source/pc/stb_vorbis.c
	${CMAKE_SOURCE_DIR}/source/pc/wav.cpp

	${CMAKE_SOURCE_DIR}/source/3ds/cbmd.cpp
	${CMAKE_SOURCE_DIR}/source/3ds/cwav.cpp
	${CMAKE_SOURCE_DIR}/source/3ds/lz11.cpp
)

set(INCLUDES
	${CMAKE_SOURCE_DIR}/source
	${CMAKE_SOURCE_DIR}/source/pc
	${CMAKE_SOURCE_DIR}/source/3ds
)

add_executable(bannertool ${SOURCES})
include_directories(bannertool ${INCLUDES})
target_compile_definitions(bannertool PRIVATE
	VERSION_MAJOR=${PROJECT_VERSION_MAJOR}
	VERSION_MINOR=${PROJECT_VERSION_MINOR}
	VERSION_MICRO=${PROJECT_VERSION_PATCH}
)