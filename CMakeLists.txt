#  set minimum cmake version
cmake_minimum_required(VERSION 3.27.4)

#  project name and language
project(options LANGUAGES CXX)

#  expose option to the user
option(USE_LIBRARY "Compile sources into a library" OFF)

message(STATUS "Compile sources into library? ${USE_LIBRARY}")

include(CMakeDependentOption)

#  second option depends on the value of the first
cmake_dependent_option(
	MAKE_STATIC_LIBRARY "Compile sources into a library" OFF
	"USE_LIBRARY" ON
	)
	
#  third option depends on the value of the first
cmake_dependent_option(
	MAKE_SHARED_LIBRARY "Compile sources into library" ON
	"USE_LIBRARY" ON
	)

set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)

# list sources
list(APPEND _sources Message.hpp Message.cpp)

if(USE_LIBRARY)
	message(STATUS "Compile source into a STATIC library? ${MAKE_STATIC_LIBRARY}")
	message(STATUS "Compile sources into a SHARED library? ${MAKE_SHARED_LIBRARY}")
	
	# create executable from hello-world.cpp
	add_executable(hello-world hello-world.cpp)
	
	if(MAKE_SHARED_LIBRARY)
		# create a shared library
		add_library(message SHARED ${_sources})
		
		# link executable to shared library
		target_link_libraries(hello-world PRIVATE message)
	endif()
	
	if(MAKE_STATIC_LIBRARY)
		# create a static library
		add_library(message SHARED ${_sources})
		
		# link executable to static library
		target_link_libraries(hello-world PRIVATE message)
	endif()
else()
	# create executable from all sources
	add_executable(hello-world hello-world.cpp ${_sources})
endif()
