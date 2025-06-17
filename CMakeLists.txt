cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/OUTPUT/${PROJECT_NAME}")
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

project(MYPROJECT LANGUAGES CXX)

add_subdirectory(deps)

file(GLOB_RECURSE SRC_FILES src/*.cpp src/*.hpp)
add_executable(${PROJECT_NAME} ${SRC_FILES}) 

target_include_directories(${PROJECT_NAME} PUBLIC
    src/
    deps/
    deps/SDL3/
    ${SDL3_INCLUDE_DIRS}
)

target_link_libraries(${PROJECT_NAME} PUBLIC
    SDL3::SDL3
)
