cmake_minimum_required(VERSION 2.8.10)

project(libB)

#find_package(Boost
 #            1.50.0
 #            REQUIRED)

file(GLOB C_FILES src/*.c)

#include_directories(${Boost_INCLUDE_DIRS})

add_library(${PROJECT_NAME} STATIC ${C_FILES})

# Required on Unix OS family to be able to be linked into shared libraries.
set_target_properties(${PROJECT_NAME}
                      PROPERTIES POSITION_INDEPENDENT_CODE ON)

target_link_libraries(${PROJECT_NAME})

# Expose B's public includes (including Boost transitively) to other
# subprojects through cache variable.
set(${PROJECT_NAME}_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/include
    CACHE INTERNAL "${PROJECT_NAME}: Include Directories" FORCE)
