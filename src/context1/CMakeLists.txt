cmake_minimum_required(VERSION 3.12)

set(CMAKE_CXX_STANDARD 20)

add_library(context1 STATIC 
        task1.cpp
)

add_executable(test_task1 test_task1.cpp)

target_link_libraries(test_task1 PRIVATE 
        context1 
        gtest_main
)

enable_testing()
add_test(NAME test_task1 COMMAND test_task1)