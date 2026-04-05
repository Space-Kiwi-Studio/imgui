cmake_minimum_required(VERSION 3.16)
project(ImGui)

# C++ config
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# ImGui source dir
set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR})

# ImGui source
set(IMGUI_SOURCES
        ${IMGUI_DIR}/imgui.cpp
        ${IMGUI_DIR}/imgui_draw.cpp
        ${IMGUI_DIR}/imgui_tables.cpp
        ${IMGUI_DIR}/imgui_widgets.cpp
        ${IMGUI_DIR}/imgui_demo.cpp
)

# Make ImGui lib
add_library(imgui STATIC ${IMGUI_SOURCES})

# Include dir
target_include_directories(imgui PUBLIC
        ${IMGUI_DIR}
)

# Compiler flags
if(MSVC)
    target_compile_options(imgui PRIVATE /W4)
else()
    target_compile_options(imgui PRIVATE -Wall -Wextra -Wpedantic)
endif()
