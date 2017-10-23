cmake_minimum_required(VERSION 2.8)
 
project(sha C)

option(ENABLE_TEST "activa la generacion de los test" OFF)

file(GLOB src
    "*.h"
    "*.c"
)
file(GLOB src_test
    "shatest.c"
)

LIST(REMOVE_ITEM src ${src_test})

add_library(${PROJECT_NAME} ${src})
target_link_libraries(shatest ${PROJECT_NAME})


if(ENABLE_TEST)
    add_executable(shatest ${src_test})

    target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

endif()
