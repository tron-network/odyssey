file(GLOB HEADERS "include/odyssey/delayed_node/*.hpp")

add_library( odyssey_delayed_node
             delayed_node_plugin.cpp
           )

target_link_libraries( odyssey_delayed_node odyssey_chain odyssey_protocol odyssey_app )
target_include_directories( odyssey_delayed_node
                            PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include" )

if(MSVC)
  set_source_files_properties( delayed_node_plugin.cpp PROPERTIES COMPILE_FLAGS "/bigobj" )
endif(MSVC)

install( TARGETS
   odyssey_delayed_node

   RUNTIME DESTINATION bin
   LIBRARY DESTINATION lib
   ARCHIVE DESTINATION lib
)
