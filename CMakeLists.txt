project (ev3 CXX)

cmake_minimum_required(VERSION 2.8)
list ( APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake )

option(BUILD_SHARED_LIBS "shared/static" ON)

enable_testing()
find_package(muParser)
add_subdirectory(lib)

