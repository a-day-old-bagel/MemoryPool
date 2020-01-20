# Set required version and policy version
cmake_minimum_required( VERSION 3.9.2 FATAL_ERROR )
cmake_policy( VERSION 3.9.2...3.16 )

# Prohibit screwing up the source tree
set( CMAKE_DISABLE_IN_SOURCE_BUILD ON )
set( CMAKE_DISABLE_SOURCE_CHANGES ON )

# Use C++11 everywhere
set( CMAKE_CXX_STANDARD 11 )
set( CMAKE_CXX_STANDARD_REQUIRED ON )

# Name the project and set a prefix for naming internal targets and variables
project( memoryPool VERSION 0.01.01.01 LANGUAGES CXX C )

add_library( ${PROJECT_NAME} INTERFACE )
target_include_directories( memoryPool INTERFACE ${CMAKE_CURRENT_SOURCE_DIR} )

option( MEMORYPOOL_BUILD_TEST "Build Memory Pool Test" ON )
if ( MEMORYPOOL_BUILD_TEST )
  add_executable( ${PROJECT_NAME}Test
    test.cpp
    )
  target_link_libraries( ${PROJECT_NAME}Test PUBLIC
    ${PROJECT_NAME}
    )
endif()
