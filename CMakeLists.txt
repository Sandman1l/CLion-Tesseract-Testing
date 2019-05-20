cmake_minimum_required(VERSION 3.13)
project(Tess)

set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_EXTENSIONS OFF)

find_package( PkgConfig REQUIRED)

pkg_search_module( TESSERACT REQUIRED tesseract )

pkg_search_module( LEPTONICA REQUIRED leptonica )

include_directories( ${TESSERACT_INCLUDE_DIRS} )

include_directories( ${LEPTONICA_INCLUDE_DIRS} )

link_directories( ${TESSERACT_LIBRARY_DIRS} )

link_directories( ${LEPTONICA_LIBRARY_DIRS} )

find_package( OpenCV REQUIRED )

include_directories("Tess.h")

file(GLOB SOURCES "Tess.cpp")

add_executable(Tess main.cpp)

target_link_libraries( Tess ${OpenCV_LIBRARIES} )

target_link_libraries( Tess ${TESSERACT_LIBRARIES} )

target_link_libraries( Tess ${LEPTONICA_LIBRARIES} )