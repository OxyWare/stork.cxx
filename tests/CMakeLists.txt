# GLFW
set(GLFW_BUILD_EXAMPLES OFF)
set(GLFW_BUILD_TESTS OFF)
set(GLFW_BUILD_DOCS OFF)
set(GLFW_INSTALL OFF)
add_subdirectory(${oxy_stork_SOURCE_DIR}/deps/glfw
        ${CMAKE_CURRENT_BINARY_DIR}/deps/glfw)

# glad
add_library(glad ${oxy_stork_SOURCE_DIR}/deps/glad/src/glad.c)
target_include_directories(glad
        PRIVATE ${oxy_stork_SOURCE_DIR}/deps/glad/include)


set(oxy_stork_entry_test_src
        entry_test.cxx)

add_executable(oxy_stork_entry_test ${oxy_stork_entry_test_src})

target_include_directories(oxy_stork_entry_test PRIVATE
        ${oxy_stork_SOURCE_DIR}/deps/glad/include
        ${oxy_stork_SOURCE_DIR}/deps/glfw/include
        ${oxy_stork_SOURCE_DIR}/include/)

target_link_libraries(oxy_stork_entry_test
        PRIVATE glfw glad stork)