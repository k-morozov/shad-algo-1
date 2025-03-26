cmake_minimum_required(VERSION 3.12)
project(shad-algo)

set(CMAKE_CXX_STANDARD 20)

add_compile_options(-Wall -Wextra -Werror -pedantic)

set(CMAKE_CXX_FLAGS_ASAN "-g -fsanitize=address,undefined -fno-sanitize-recover=all"
        CACHE STRING "Compiler flags in asan build"
        FORCE)

add_subdirectory(contrib/googletest)

add_library(context1 STATIC src/context1/task1.h src/context1/task1.cpp)

target_include_directories(context1 PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}/src/context1
)

add_executable(test_context1 src/context1/test_task1.cpp)

target_link_libraries(test_context1 PRIVATE 
        context1 
        gtest_main
)

enable_testing()
add_test(NAME test_task1 COMMAND test_context1)