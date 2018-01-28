cmake_minimum_required(VERSION 2.6)

# set project name from current directory
get_filename_component(BASENAME ${CMAKE_SOURCE_DIR} NAME)
project(${BASENAME})

set(CMAKE_BUILD_TYPE DEBUG)
set(CMAKE_C_FLAGS "-Wall -pthread -g -pipe")
set(CMAKE_CXX_FLAGS "-std=c++11 -Wall")

# define executable to build
include_directories("inc")
aux_source_directory(src SRC_FILES)
add_library(v4l2wrapper STATIC ${SRC_FILES})

# package
install(TARGETS v4l2wrapper DESTINATION /usr/lib)
install(DIRECTORY inc/ DESTINATION /usr/include)
