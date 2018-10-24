################################################################################
# CMakeLists.txt
#
# Example for Project Thrill - http://project-thrill.org
#
# Copyright (C) 2018 Timo Bingmann <tb@panthema.net>
#
# All rights reserved. Published under the BSD-2 license in the LICENSE file.
################################################################################

# require cmake 2.8.0
cmake_minimum_required(VERSION 2.8.0)

# we first give our project a name
project(sample-project)

# prohibit in-source builds
if("${PROJECT_SOURCE_DIR}" STREQUAL "${PROJECT_BINARY_DIR}")
  message(SEND_ERROR "In-source builds are not allowed.")
endif("${PROJECT_SOURCE_DIR}" STREQUAL "${PROJECT_BINARY_DIR}")

# enable warnings (always good)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -W -Wall")

# include Thrill as cmake subproject
add_subdirectory(extlib/thrill)

# create and executable and link with Thrill (all flags and includes are added)
add_executable(word_count word_count.cpp)
target_link_libraries(word_count thrill)

################################################################################
