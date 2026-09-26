cmake_minimum_required(VERSION 3.21)
project(gdc++ VERSION 1.0.0)

add_library(${PROJECT_NAME} SHARED src/main.cpp src/CodeEditor.cpp src/MenuLayer.cpp)

target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_20)

# Geode
target_link_libraries(${PROJECT_NAME} PUBLIC geode::geode)

# ChaiScript (header-only)
include(FetchContent)
FetchContent_Declare(
    chaiscript
    GIT_REPOSITORY https://github.com/ChaiScript/ChaiScript.git
    GIT_TAG v6.1.0
)
FetchContent_MakeAvailable(chaiscript)
target_include_directories(${PROJECT_NAME} PRIVATE ${chaiscript_SOURCE_DIR}/include)
