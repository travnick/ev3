project (ev3 CXX)
set(project_dir ${ev3_SOURCE_DIR})

cmake_minimum_required(VERSION 2.8)
list ( APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake )

if (NOT ${CMAKE_BUILD_TYPE} STREQUAL "")
	set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${project_dir}/${CMAKE_BUILD_TYPE}/bin)
	set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${project_dir}/${CMAKE_BUILD_TYPE}/lib)
	set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${project_dir}/${CMAKE_BUILD_TYPE}/lib)
	link_directories(${CMAKE_ARCHIVE_OUTPUT_DIRECTORY})
else()
	set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${project_dir}/Debug/bin)
	set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG ${project_dir}/Debug/lib)
	set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${project_dir}/Debug/lib)
	link_directories(${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG})

	set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${project_dir}/Release/bin)
	set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_RELEASE ${project_dir}/Release/lib)
	set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${project_dir}/Release/lib)
	link_directories(${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE})
endif()

option(BUILD_SHARED_LIBS "shared/static" ON)
set(BUILD_TESTS OFF CACHE BOOL "Build test project?")

find_package(Boost REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})

add_subdirectory(lib)

if (${BUILD_TESTS})
	enable_testing()
	add_subdirectory("lib/test")
endif()
