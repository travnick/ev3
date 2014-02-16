set (src/headers src/auxiliary.h src/common.h src/exceptions.h  src/expression.h src/parser.h)
set(sources src/expression.cxx src/parser.cxx )

add_library(ev3 ${sources})
if (MINGW AND BUILD_SHARED_LIBS)
  set_target_properties(ev3 PROPERTIES SUFFIX "-1.dll")
endif()

install (TARGETS ev3 RUNTIME DESTINATION bin
                          LIBRARY DESTINATION lib${LIB_SUFFIX}
                          ARCHIVE DESTINATION lib${LIB_SUFFIX})

install (FILES ${headers} DESTINATION include)


add_subdirectory(test)