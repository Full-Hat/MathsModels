cmake_minimum_required(VERSION 3.5.0)

# Set global flags
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake)
set(CMAKE_CXX_STANDARD 20)

set(PROJECT_NAME MathsModels)

project(${PROJECT_NAME} VERSION 0.0.1 LANGUAGES C CXX)

# executable file
# add main library file for engine
add_executable(binary main.cpp)

add_executable(test.exe test/test.cpp)
add_test(test test.exe)

# test section with other executables
enable_testing()

find_package(GTest REQUIRED)
target_link_libraries(test.exe PRIVATE GTest::gtest GTest::gtest_main GTest::gmock GTest::gmock_main)
