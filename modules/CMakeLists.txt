set(modules
        libA
        root
)

foreach (module ${modules})
    add_subdirectory(${module})
endforeach ()

add_library(modules SHARED modules.cpp)
target_include_directories(modules PUBLIC root)
target_link_libraries(modules PUBLIC root)

file(GLOB_RECURSE MY_PUBLIC_HEADERS
        "*.h"
)
message(STATUS "headers: ${MY_PUBLIC_HEADERS}")
file(COPY ${MY_PUBLIC_HEADERS} DESTINATION ${CMAKE_BINARY_DIR}/out/include)