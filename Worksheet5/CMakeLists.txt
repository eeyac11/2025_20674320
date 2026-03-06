cmake_minimum_required(VERSION 3.12 FATAL_ERROR)
project(calc)

if( NOT BUILD_SHARED_LIBS)
add_definitions(-Dmaths_STATIC)
endif()


if(WIN32)
	set(CPACK_GENERATOR "NSIS")
else()
	set(CPACK_GENERATOR "ZIP")
endif()

include(CPack)

add_library(maths adder.cpp)

add_executable(calc calc.cpp)
target_link_libraries(calc maths)

install( TARGETS calc maths
RUNTIME DESTINATION bin
LIBRARY DESTINATION lib
ARCHIVE DESTINATION lib/static)