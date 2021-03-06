cmake_minimum_required(VERSION 3.4)

set(PROJECT_NAME glittering_moon)
set(BUILD_VERSION 0.0)

project(${PROJECT_NAME})

set(CMAKE_BINARY_DIR "${CMAKE_CURRENT_SOURCE_DIR}/build")

set(CMAKE_CXX_FLAGS "-std=c++14 -O3 -W -Wall -Wextra --pedantic -Wno-comment -Werror -lfcgi -lfcgi++")

if (CMAKE_BUILD_TYPE MATCHES "Debug")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
endif(CMAKE_BUILD_TYPE MATCHES "Debug")


set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake/Module")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

file(GLOB_RECURSE SOURCE src/*.cpp include/*.h include/*.hpp)
set(SOURCE_FILES main.cpp ${SOURCE})

set(EXECUTABLE_NAME ${PROJECT_NAME}-${BUILD_VERSION}-${CMAKE_BUILD_TYPE}.fastCGI)

add_executable(${EXECUTABLE_NAME} ${SOURCE_FILES})
