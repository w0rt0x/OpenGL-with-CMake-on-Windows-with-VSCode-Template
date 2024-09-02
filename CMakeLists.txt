# Standard Cmake Setup
cmake_minimum_required(VERSION 3.5.0)
project(PONG VERSION 0.1.0 LANGUAGES C CXX)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Project structure: Add Subdirs with other CMake Lists
add_subdirectory(src)
add_subdirectory(libs)
add_subdirectory(include)

# Make CMake aware of the libs folder with pre compiled Binaries
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw)

set(SRC_FILES src/main.cpp src/glad/glad.c)
add_executable(Pong ${SRC_FILES})

# Add Header Files from Include Dir
target_include_directories(Pong PRIVATE include)

# Linking Glad and GLFW3 to Executable
target_link_libraries(Pong PRIVATE glad glfw3)

# Copy the GLFW3.dll to the output directory
add_custom_command(TARGET Pong POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    "${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/glfw3.dll"
    $<TARGET_FILE_DIR:Pong>
)
