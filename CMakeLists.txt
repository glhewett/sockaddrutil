cmake_minimum_required(VERSION 3.17)
set(LIB_NAME sockaddrutil)
project(${LIB_NAME} C)

set(CMAKE_C_STANDARD 99)

include_directories(include)

set( ${LIB_NAME}_srcs
        src/sockaddrutil.c
        include/sockaddrutil.h )

add_library(${LIB_NAME}  ${${LIB_NAME}_srcs} )

install(TARGETS ${LIB_NAME} EXPORT ${LIB_NAME}Targets
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION lib
        INCLUDES destination include)

install(EXPORT ${LIB_NAME}Targets
        FILE ${${LIB_NAME}Targets}.cmake
        NAMESPACE ${LIB_NAME}
        DESTINATION lib/cmake/${LIB_NAME})

add_subdirectory ( test )