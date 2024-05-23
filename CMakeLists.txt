cmake_minimum_required(VERSION 3.10)
project(3d_modeling_app)

set(CMAKE_C_STANDARD 11)

# Find packages
find_package(OpenGL REQUIRED)
find_package(glfw3 3.3 REQUIRED)

# Find GLEW manually
find_path(GLEW_INCLUDE_DIR GL/glew.h PATHS /opt/homebrew/Cellar/glew/*/include)
find_library(GLEW_LIBRARY libGLEW.dylib PATHS /opt/homebrew/Cellar/glew/*/lib)

# Include directories
include_directories(${OPENGL_INCLUDE_DIRS} ${GLEW_INCLUDE_DIRS} ${GLFW_INCLUDE_DIRS} include)

# Source files
file(GLOB SOURCES "src/*.c")

# Executable
add_executable(3d_modeling_app ${SOURCES})

# Link libraries
target_link_libraries(3d_modeling_app ${OPENGL_LIBRARIES} ${GLEW_LIBRARY} glfw)