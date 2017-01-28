project( TryEigen )
cmake_minimum_required( VERSION 2.8.3 )

configure_file(
    "${PROJECT_SOURCE_DIR}/Configs.h.in"
    "${PROJECT_BINARY_DIR}/Configs.h" )
include_directories( ${CMAKE_BINARY_DIR}/ )

set( EIGEN3_INCLUDE_DIR "$ENV{EIGEN3_INCLUDE_DIR}" )
if( NOT EIGEN3_INCLUDE_DIR )
    message( STATUS "Use Repo Eigen." )
    set( EIGEN3_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include" )
else()
    message( STATUS "Use System Eigen." )
endif()
include_directories( "${EIGEN3_INCLUDE_DIR}" )

file( GLOB SRCS src/*.cpp)
foreach( src ${SRCS} )
    string( REGEX REPLACE "(^.*/|.cpp$)" "" exe ${src} )
    message( STATUS "${exe} <-- ${src}" )
    add_executable( ${exe} ${src} )
endforeach( src )
