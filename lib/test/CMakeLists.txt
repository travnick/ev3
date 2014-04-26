find_package(muParser REQUIRED)
include_directories(${CMAKE_SOURCE_DIR}/lib/src ${MUPARSER_INCLUDE_DIRS})

add_executable(t_ev3_std t_ev3_std.cxx)
target_link_libraries(t_ev3_std
	ev3
	${MUPARSER_LIBRARIES}
)

add_test(NAME t_ev3_std COMMAND t_ev3_std)
