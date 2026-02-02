cmake_minimum_required(VERSION 3.14)
project(ukf_project LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 源文件 - 使用 src/ 目录
file(GLOB SOURCES "${CMAKE_SOURCE_DIR}/src/*.cpp")
list(SORT SOURCES)

add_executable(main ${SOURCES})
target_include_directories(main PRIVATE ${CMAKE_SOURCE_DIR})

# 编译选项
target_compile_options(main PRIVATE
    -Wall -Wextra -Wpedantic
    -Werror=return-type
)

# 依赖 Eigen3
find_package(Eigen3 REQUIRED)
target_link_libraries(main PRIVATE Eigen3::Eigen)
