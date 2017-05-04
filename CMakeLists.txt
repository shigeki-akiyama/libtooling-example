cmake_minimum_required(VERSION 2.8)
project(example)

find_package(LLVM REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

add_definitions("-std=c++14 -Wall -Wextra -Wno-unused -Wno-comment -fno-exceptions -fno-rtti")

add_definitions(${LLVM_DEFINITIONS})
include_directories(${LLVM_INCLUDE_DIRS})
link_directories(${LLVM_LIBRARY_DIRS})

add_executable(example example.cpp)

target_link_libraries(
    example
    clangRewrite
    clangTooling
    clangDriver
    clangFrontend
    clangSerialization
    clangParse
    clangSema
    clangEdit
    clangAnalysis
    clangLex
    clangAST
    clangBasic
    LLVM-4.0
)

