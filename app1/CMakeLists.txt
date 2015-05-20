cmake_minimum_required(VERSION 2.8.10)

project(app1 C)

file(GLOB C_FILES src/*.c)

add_definitions(${libA_DEFINITIONS} ${libB_DEFINITIONS})

include_directories(${libA_INCLUDE_DIRS} ${libB_INCLUDE_DIRS})

add_executable(${PROJECT_NAME} ${C_FILES})

target_link_libraries(${PROJECT_NAME} libA libB)
