
cmake_minimum_required(VERSION 3.22)

project(exp)

enable_language(ASM)

set(C_FLAGS
    -Wall
    -Wextra
    -Wmost
    -fno-stack-protector
    -fomit-frame-pointer
)

set(CMAKE_ASM_FLAGS "${CMAKE_ASM_FLAGS} -I${CMAKE_CURRENT_SOURCE_DIR}")

add_library(exp SHARED exp.c stage1.S elf_parser.c)

target_compile_options(exp PRIVATE ${C_FLAGS})

target_include_directories(exp PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")

target_link_libraries(exp log)
