cmake_minimum_required(VERSION 3.16.0)

project(proto)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out/bin)

add_subdirectory(modules)
include_directories(modules)

add_executable(main main.cpp)
target_link_libraries(main PUBLIC
        modules
    )

file(GLOB MODULES_HEADERS
        "${CMAKE_CURRENT_BINARY_DIR}/modules/includes/*.h"
)
message(STATUS "headers: ${MODULES_HEADERS}")
file(COPY ${MODULES_HEADERS} DESTINATION ${CMAKE_BINARY_DIR}/out/include)