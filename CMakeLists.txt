cmake_minimum_required(VERSION 3.10)
project(SystemIdentificationProject)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 查找 GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

# 添加子目录
add_subdirectory(src/system_identification)
add_subdirectory(lib/mathlib)
