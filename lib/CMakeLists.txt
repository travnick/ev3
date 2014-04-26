
set ( headers src/auxiliary.h src/common.h src/exceptions.h  src/expression.h src/parser.h )
set ( sources src/parser.cxx src/expression.cxx src/operand.cxx )

add_library ( ev3 ${sources} ${headers} )
if ( MINGW AND BUILD_SHARED_LIBS )
  set_target_properties ( ev3 PROPERTIES SUFFIX "-1.dll" )
endif ()

install ( TARGETS ev3
          RUNTIME DESTINATION bin
          LIBRARY DESTINATION lib${LIB_SUFFIX}
          ARCHIVE DESTINATION lib${LIB_SUFFIX} )

install ( FILES ${headers} DESTINATION include )
