cmake_minimum_required(VERSION 3.20)
project(ImGui)

set(SOURCES
    "imgui.cpp"
    "imgui_draw.cpp"
    "imgui_widgets.cpp"
    "imgui_tables.cpp"
    "imgui_demo.cpp"
    "imgui_impl_glfw.cpp"
    "imgui_impl_vulkan.cpp"
)

set(HEADERS
   "imconfig.h"
   "imgui.h"
   "imgui_internal.h"
   "imstb_rectpack.h"
   "imstb_textedit.h"
   "imstb_truetype.h"
   "imgui_impl_glfw.h"
   "imgui_impl_vulkan.h"
)

add_library(ImGui STATIC
    ${SOURCES}
    ${HEADERS}
)

target_include_directories(ImGui PUBLIC
    "."
    ${Vulkan_INCLUDE_DIRS}
)

target_link_libraries(ImGui PRIVATE
    glfw
    ${Vulkan_LIBRARIES}
)
