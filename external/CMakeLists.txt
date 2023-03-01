include(FetchContent)
set(FETCHCONTENT_QUIET NO)

if (NOT sfml_FOUND)
    FetchContent_Declare(
            sfml
            GIT_REPOSITORY "https://github.com/SFML/SFML"
            GIT_TAG 2.5.x
            SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/SFML
    )
    message(STATUS "Fetching SFML")
    FetchContent_MakeAvailable(sfml)
endif ()

if (NOT imgui_FOUND)
    FetchContent_Declare(
            imgui
            GIT_REPOSITORY https://github.com/ocornut/imgui
            GIT_TAG 375ae5dce46fca73838832dac1e3bd0f3b4727f5
            SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/imgui
    )
    message(STATUS "Fetching ImGui")
    FetchContent_MakeAvailable(imgui)
endif ()

if (NOT imgui-sfml)
    FetchContent_Declare(
            imgui-sfml
            GIT_REPOSITORY https://github.com/eliasdaler/imgui-sfml
            GIT_TAG 49dbecb43040449cccb3bfc43e3472cee94da417
            SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/imgui-sfml
    )
    message(STATUS "Fetching ImGui-SFML")
    set(IMGUI_DIR ${imgui_SOURCE_DIR})
    set(IMGUI_SFML_FIND_SFML OFF)
    set(IMGUI_SFML_IMGUI_DEMO ON)
    FetchContent_MakeAvailable(imgui-sfml)
endif ()