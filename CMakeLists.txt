cmake_minimum_required(VERSION 3.12)
project(lv_web_test C CXX)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O2 -s USE_SDL=2")

add_subdirectory(lib/lvgl)

add_executable(index
        ${PROJECT_SOURCE_DIR}/src/main.cpp
)
target_include_directories(lvgl PUBLIC ${PROJECT_SOURCE_DIR})

set(CMAKE_EXECUTABLE_SUFFIX ".html")

target_link_libraries(index
        lvgl
        SDL2
)
set_target_properties(index PROPERTIES LINK_FLAGS "--shell-file \"${PROJECT_SOURCE_DIR}/src/lvgl_shell.html\" -s SINGLE_FILE=1 -s INITIAL_MEMORY=33554432")