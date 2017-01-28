project( TryEigen )
cmake_minimum_required( VERSION 2.8.3 )

configure_file(
    "${PROJECT_SOURCE_DIR}/Configs.h.in"
    "${PROJECT_BINARY_DIR}/Configs.h" )
include_directories( ${CMAKE_SOURCE_DIR}/ )
include_directories( ${CMAKE_BINARY_DIR}/ )

file( GLOB SRCS src/*.cpp)
foreach( src ${SRCS} )
    string( REGEX REPLACE "(.*/|.cpp$)" "" exe ${src} )
    message( STATUS "${exe} <-- ${src}" )
    add_executable( ${exe} ${src} )
endforeach( src )
