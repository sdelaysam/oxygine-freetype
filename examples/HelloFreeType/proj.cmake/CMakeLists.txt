cmake_minimum_required (VERSION 2.6)
project (HelloFreeType)

add_subdirectory(../../../../oxygine-framework/ oxygine-framework)
add_definitions(${OXYGINE_DEFINITIONS})
include_directories(${OXYGINE_INCLUDE_DIRS})
link_directories(${OXYGINE_LIBRARY_DIRS})

add_subdirectory(../../../../oxygine-freetype/ oxygine-freetype)
include_directories(${OXYGINE_FREETYPE_INCLUDE_DIRS})
link_directories(${OXYGINE_FREETYPE_LIBRARY_DIRS})

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
add_executable(HelloFreeType ../src/entry_point.cpp ../src/example.cpp  ../src/example.h )

if (WIN32) #disable console mode for VC++
	set_target_properties(HelloFreeType PROPERTIES WIN32_EXECUTABLE TRUE)
endif(WIN32)

target_link_libraries(HelloFreeType ${OXYGINE_CORE_LIBS} ${OXYGINE_FREETYPE_LIBS} oxygine-freetype freetype)
