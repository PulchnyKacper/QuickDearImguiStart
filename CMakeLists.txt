cmake_minimum_required(VERSION 3.10)
project(ImGuiProject)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(ENV{CMAKE_PREFIX_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/glfw3;$ENV{CMAKE_PREFIX_PATH}")
find_package(glfw3 3.3 REQUIRED)
find_package(OpenGL REQUIRED)

include_directories(${OPENGL_INCLUDE_DIR})
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/imgui)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/glad/include)

file(GLOB IMGUI_SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp"
)

set(GLAD_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/glad/src/glad.c)

add_executable(${PROJECT_NAME} main.cpp ${IMGUI_SOURCES} ${GLAD_SOURCES})
target_link_libraries(${PROJECT_NAME} glfw ${OPENGL_gl_LIBRARY})