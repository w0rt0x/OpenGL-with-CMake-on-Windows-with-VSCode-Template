add_subdirectory(glad)
add_subdirectory(GLFW)
add_subdirectory(KHR)

add_library(glad STATIC glad/glad.h)
target_include_directories(glad PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include/glad
)

add_library(glfw SHARED GLFW/glfw3.h GLFW/glfw3native.h)

# Avoid Linker Error
set_target_properties(glad PROPERTIES LINKER_LANGUAGE CXX)
set_target_properties(glfw PROPERTIES LINKER_LANGUAGE CXX)
#set(CMAKE_INCLUDE_CURRENT_DIR ON)
