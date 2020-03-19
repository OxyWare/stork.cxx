cmake_minimum_required(VERSION 3.15)

project(oxy_stork
        VERSION 0.0.0
        DESCRIPTION "2D vector graphics library on top of OpenGL/DirectX/Vulkan."
        LANGUAGES CXX C)

# Against in-source builds
if (${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR})
    message(FATAL_ERROR "In-source builds not allowed. Please make a new directory and run cmake there.")
endif()

set(oxy_stork_SOURCE_DIR ${CMAKE_SOURCE_DIR})

if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()

option(BUILD_TESTS "Build the tests" ON)

if (BUILD_TESTS)
    enable_testing()
    include(GoogleTest)
    # Build google mock and tests (targets: gmock, gtest, gmock_main, gtest_main)
    add_subdirectory(deps/googletest)
    add_subdirectory(tests)
endif()

add_subdirectory(src)