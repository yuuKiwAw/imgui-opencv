cmake_minimum_required(VERSION 3.0.0)
project(imgui-opencv VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 17)
include_directories(${PROJECT_SOURCE_DIR}/include)
LINK_DIRECTORIES(${CMAKE_SOURCE_DIR}/lib)

IF(WIN32)
    SET(DCMAKE_TOOLCHAIN_FILE "E:/vcpkg/scripts/buildsystems/vcpkg.cmake")
    include("E:/vcpkg/scripts/buildsystems/vcpkg.cmake")
ENDIF()

find_package(OpenCV REQUIRED)
find_package(glfw3 REQUIRED)
find_package(imgui REQUIRED)

aux_source_directory(./src SrcFiles)
set(EXECUTABLE_OUTPUT_PATH  ${PROJECT_SOURCE_DIR}/build)
add_executable(main ${SrcFiles})

target_link_libraries(main ${OpenCV_LIBS} glfw opengl32.lib imgui::imgui)