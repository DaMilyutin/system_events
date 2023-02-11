cmake_minimum_required(VERSION 3.13)

project(system_events)

enable_testing()

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/_bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/_bin)

add_compile_options(
	"$<$<CXX_COMPILER_ID:GNU,Clang,AppleClang>:-fPIC;-Wpedantic;-Wall;-Wextra;-Wno-long-long;-std=c++03>"
	"$<$<NOT:$<CXX_COMPILER_ID:MSVC>>:$<$<CONFIG:Release,RelWithDebInfo>:-O3>>"
	"$<$<CXX_COMPILER_ID:MSVC>:$<$<CONFIG:Release,RelWithDebInfo>:-Ox;-W4>>"
)
add_definitions(-D_SCL_SECURE_NO_WARNINGS -D_CRT_SECURE_NO_WARNINGS)

add_library(system_events INTERFACE)
target_include_directories(system_events INTERFACE ./include/.)
