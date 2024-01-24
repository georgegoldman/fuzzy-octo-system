# The first thing we will do is declare the requirement on minimum version of CMake
cmake_minimum_required(VERSION 3.27.4)

# Next, we declare our project and its programming language
project(Hello VERSION 1.0)

# We create an executable target. CMake will generate rules in the build system to compile and link our source file into an executable
add_executable(hello main.cc)

