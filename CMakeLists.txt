cmake_minimum_required(VERSION 3.28)
project(CCHIPP-8 LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

include(FetchContent)
# SFML
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 3.1.0
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(SFML)

# Catch2
FetchContent_Declare(
        Catch2
        GIT_REPOSITORY https://github.com/catchorg/Catch2.git
        GIT_TAG        v3.8.1 # or a later release
)
FetchContent_MakeAvailable(Catch2)

add_executable(cchipp-8 src/main.cpp)
target_compile_features(cchipp-8 PRIVATE cxx_std_17)
target_link_libraries(cchipp-8 PRIVATE SFML::Graphics)
target_link_libraries(cchipp-8 PRIVATE Catch2::Catch2WithMain)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT main)
