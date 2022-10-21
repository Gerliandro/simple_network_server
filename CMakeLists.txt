cmake_minimum_required(VERSION 3.10)
project(simple_server VERSION 1.0 LANGUAGES CXX)

message(STATUS "Project: ${PROJECT_NAME} (version ${CMAKE_PROJECT_VERSION})")
message(STATUS "Build Type: ${CMAKE_BUILD_TYPE}")
message(STATUS "CMake Generator: ${CMAKE_GENERATOR}")

include(FetchContent)

set(CMAKE_CXX_STANDARD 11) 
set(CMAKE_CXX_EXTENSIONS ON) 
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin/${CMAKE_BUILD_TYPE}/)
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin/${CMAKE_BUILD_TYPE}/)

include_directories(${PROJECT_SOURCE_DIR}/include)

file(GLOB_RECURSE SRCS RELATIVE ${PROJECT_SOURCE_DIR} "src/*.cpp")

add_executable(
    ${PROJECT_NAME}
    ${SRCS}
)

target_link_libraries(
    ${PROJECT_NAME}
)

target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR}/include)
