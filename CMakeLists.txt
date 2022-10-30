cmake_minimum_required(VERSION 3.23)
project(HelloSFML)
set(CMAKE_CXX_STANDARD 23)

# Setup build directory
math(EXPR platform_bits "${CMAKE_SIZEOF_VOID_P} * 8")
set(platform_dir ${CMAKE_SYSTEM_NAME}${platform_bits})
set(project_platform_binary_dir ${CMAKE_SOURCE_DIR}/bin/${platform_dir}/$<CONFIG>)
# Set .dll/.exe files directory
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${project_platform_binary_dir})

# Setup cache directory
set(CMAKE_BUILD_FILES_DIRECTORY ${CMAKE_SOURCE_DIR}/bin/intermediate/${platform_dir}/$<CONFIG>)
set(CMAKE_BUILD_DIRECTORY ${CMAKE_SOURCE_DIR}/bin/intermediate/${platform_dir}/$<CONFIG>)
SET(CMAKE_CACHEFILE_DIR ${CMAKE_SOURCE_DIR}/bin/intermediate/${platform_dir}/$<CONFIG>)

file(MAKE_DIRECTORY ${CMAKE_SOURCE_DIR}/include)
file(MAKE_DIRECTORY ${CMAKE_SOURCE_DIR}/src)
# Search for .cpp files
file(GLOB_RECURSE SRC_FILES ${CMAKE_SOURCE_DIR}/src/*.cpp)

add_executable(${PROJECT_NAME} ${SRC_FILES})

set(BUILD_SHARED_LIBS ON)

target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_SOURCE_DIR}/include)
target_link_libraries(${PROJECT_NAME} PRIVATE sfml-system sfml-window sfml-graphics sfml-audio sfml-network
        ImGui-SFML::ImGui-SFML)

add_subdirectory(external)