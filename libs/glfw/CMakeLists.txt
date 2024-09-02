# add the corresponding .lib and .dll files
add_library(glfw3 SHARED IMPORTED)

set_target_properties(glfw3 PROPERTIES
    IMPORTED_LOCATION "${CMAKE_CURRENT_SOURCE_DIR}/lib/glfw/lib-vc2022/glfw3dll.lib"
    IMPORTED_IMPLIB "${CMAKE_CURRENT_SOURCE_DIR}/lib/glfw/lib-vc2022/glfw3.lib"
)

# Include GLFW headers
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib/glfw/include)