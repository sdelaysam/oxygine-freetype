cmake_minimum_required (VERSION 2.6)
project (OXYGINE_FREETYPE)

if (EMSCRIPTEN)
	set(CMAKE_CXX_FLAGS "-Wno-warn-absolute-paths")
	message(status emscripten)
	set(OXYGINEMAGICPARTICLES_INCLUDE_DIRS 
		${CMAKE_CURRENT_SOURCE_DIR}/src
		${CMAKE_CURRENT_SOURCE_DIR}/magic_particles/emscripten)

	set(OXYGINEMAGICPARTICLES_LIBS
		${CMAKE_CURRENT_SOURCE_DIR}/magic_particles/emscripten/libmagic.a)

else(EMSCRIPTEN)
	set(OXYGINE_FREETYPE_INCLUDE_DIRS 
		${CMAKE_CURRENT_SOURCE_DIR}/src
		${CMAKE_CURRENT_SOURCE_DIR}/freetype/win32/include)

	set(OXYGINE_FREETYPE_LIBS
		${CMAKE_CURRENT_SOURCE_DIR}/freetype/win32/freetype.lib)
endif(EMSCRIPTEN)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

include_directories(${OXYGINE_FREETYPE_INCLUDE_DIRS})
add_library(oxygine-freetype STATIC 
	src/ResFontFT.cpp 
	src/ResFontFT.h
)

#target_link_libraries(oxyginemagicparticles)

set(OXYGINE_FREETYPE_INCLUDE_DIRS ${OXYGINE_FREETYPE_INCLUDE_DIRS} PARENT_SCOPE)
set(OXYGINE_FREETYPE_LIBS ${OXYGINE_FREETYPE_LIBS} PARENT_SCOPE)