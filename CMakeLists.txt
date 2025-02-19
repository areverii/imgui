cmake_minimum_required(VERSION 3.6)
project(imgui)

set(Vulkan_INCLUDE_DIRS
	$ENV{VULKAN_SDK}/Include
)

add_library(imgui STATIC
        imgui.cpp
        imgui_demo.cpp
        imgui_draw.cpp
        imgui_tables.cpp
        imgui_widgets.cpp
        backends/imgui_impl_glfw.cpp
        backends/imgui_impl_vulkan.cpp
        imgui_internal.h
        imstb_rectpack.h
        imstb_textedit.h
        imstb_truetype.h)

target_include_directories(imgui PRIVATE
        ${PROJECT_SOURCE_DIR}/../GLFW/include
        ${PROJECT_SOURCE_DIR}
        ${PROJECT_SOURCE_DIR}/backends
        ${Vulkan_INCLUDE_DIRS}
)

find_package(Vulkan REQUIRED)

#target_compile_options(imgui PRIVATE -Wall -Wextra -Wno-deprecated-enum-enum-conversion)
