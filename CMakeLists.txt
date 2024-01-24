cmake_minimum_required(VERSION 3.27.4)

project(cmake-syntax LANGUAGES CXX)

set(MAKE_SHARED_LIBRARY OFF)

if (MAKE_SHARED_LIBRARY)
	message(STATUS "Build shared library")
	add_library(message SHARED)
else()
	message(STATUS "Build static library")
	add_library(message STATIC)
endif()

target_sources(message
	PUBLIC
		Message.hpp
		Message.cpp
)

add_executable(hello-world Message.cpp)

target_link_libraries(hello-world PRIVATE message)
