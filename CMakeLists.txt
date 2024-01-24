cmake_minimum_required(VERSION 3.27.4)

project(cmake-syntax VERSION 1.0)

set(hello "world")
message("hello ${hello}")

include(CMakePrintHelpers)

add_executable()
