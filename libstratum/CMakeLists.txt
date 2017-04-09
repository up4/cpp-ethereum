set(EXECUTABLE ethstratum)

aux_source_directory(. SRC_LIST)

include_directories(BEFORE ${JSONCPP_INCLUDE_DIRS})
include_directories(BEFORE ..)
include_directories(${Boost_INCLUDE_DIRS})

file(GLOB HEADERS "*.h")

MESSAGE( STATUS "EXECUTABLE " ${EXECUTABLE} )
MESSAGE( STATUS "SRC_LIST " ${SRC_LIST} )
MESSAGE( STATUS "HEADERS " ${HEADERS} )

add_library(${EXECUTABLE} ${SRC_LIST} ${HEADERS})
target_link_libraries(${EXECUTABLE} ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY} ${Boost_REGEX_LIBRARY} devcore ethcore) 

install( TARGETS ${EXECUTABLE} RUNTIME DESTINATION bin ARCHIVE DESTINATION lib LIBRARY DESTINATION lib )
install( FILES ${HEADERS} DESTINATION include/${EXECUTABLE} )