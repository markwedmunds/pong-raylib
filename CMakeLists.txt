cmake_minimum_required(VERSION 3.26)
project(pong)

set(CMAKE_CXX_STANDARD 17)

add_executable(pong src/main.cpp)

target_include_directories(pong PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

find_library(RAYLIB_LIB NAMES raylib PATHS ${CMAKE_CURRENT_SOURCE_DIR}/lib NO_DEFAULT_PATH)

if (NOT RAYLIB_LIB)
    message(FATAL_ERROR "RAYLIB library not found")
endif ()

target_link_libraries(pong PRIVATE ${RAYLIB_LIB})
target_link_libraries(pong PRIVATE "-framework IOKit")
target_link_libraries(pong PRIVATE "-framework CoreFoundation")
target_link_libraries(pong PRIVATE "-framework Cocoa")
