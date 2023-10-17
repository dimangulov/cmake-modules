add_library(root SHARED "root.cpp")
target_include_directories(root PUBLIC ../libA)
target_link_libraries(root PUBLIC libA)
