cmake_minimum_required(VERSION 3.16)
project(viperfish)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 17)

if (APPLE)
   include_directories(/usr/local/include)
   link_directories(/usr/local/lib)
endif()

include_directories(${PROJECT_SOURCE_DIR}/include)

add_library(
	${PROJECT_NAME}
	STATIC
	src/viperfish_analog_bitset.cpp
	src/viperfish_animation_window.cpp
	src/viperfish_animpath_window.cpp
	src/viperfish_dear_imgui.cpp
	src/viperfish_gamepad.cpp
	src/viperfish_keyboard.cpp
	src/viperfish_loading_window.cpp
	src/viperfish_mouse.cpp
	src/viperfish_root_window.cpp
	src/viperfish_stats_window.cpp
	src/viperfish_widget.cpp
	src/viperfish_window.cpp
	src/viperfish_xinput.cpp
   )

if(${CMAKE_VERSION} VERSION_GREATER "3.16.0")
    message("Viperfish using precompiled headers")
    target_precompile_headers(${PROJECT_NAME} PRIVATE src/viperfish_pch.cpp)
endif()

find_package(GLEW REQUIRED)
target_link_libraries(${PROJECT_NAME} PRIVATE GLEW::GLEW)

