cmake_minimum_required (VERSION 3.0 FATAL_ERROR)

project(gexf LANGUAGES CXX VERSION 0.1.2)

set(CMAKE_POSITION_INDEPENDENT_CODE ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_VERBOSE_MAKEFILE OFF)

file(GLOB_RECURSE SOURCE "./libgexf/*.cpp")

get_filename_component(HEADERS "./libgexf" REALPATH)

find_package(LibXml2 REQUIRED)

include_directories(${HEADERS} ${LIBXML2_INCLUDE_DIR})
add_library(gexf STATIC ${SOURCE})
target_link_libraries (gexf ${LIBXML2_LIBRARIES})
target_compile_definitions(gexf PUBLIC ${LIBXML2_DEFINITIONS})