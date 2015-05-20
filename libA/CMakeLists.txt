cmake_minimum_required(VERSION 2.8.10)

project(libA)

#find_package(XXX REQUIRED)

file(GLOB C_FILES src/*.c)

#add_definitions(${XXX_DEFINITIONS})

# NOTE: Boost's includes are transitively added through B_INCLUDE_DIRS.
#include_directories(${B_INCLUDE_DIRS}
#                    ${XXX_INCLUDE_DIRS})

add_library(${PROJECT_NAME} SHARED ${C_FILES})

#target_link_libraries(${PROJECT_NAME} B ${XXX_LIBRARIES})

# Expose C's definitions (in this case only the ones of XXX transitively)
# to other subprojects through cache variable.
#set(${PROJECT_NAME}_DEFINITIONS ${XXX_DEFINITIONS}
#    CACHE INTERNAL "${PROJECT_NAME}: Definitions" FORCE)

# Expose C's public includes (including the ones of C's dependencies transitively)
# to other subprojects through cache variable.
#set(${PROJECT_NAME}_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/include
#                                 ${B_INCLUDE_DIRS}
#                                 ${XXX_INCLUDE_DIRS}
#   CACHE INTERNAL "${PROJECT_NAME}: Include Directories" FORCE)
set(${PROJECT_NAME}_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/include
   CACHE INTERNAL "${PROJECT_NAME}: Include Directories" FORCE)
