cmake_minimum_required(VERSION 4.0)
project(hello-world VERSION 0.1 LANGUAGES CXX)
Include(FetchContent)

# ~~~~~~~~~~~~~~~~~~~~~~~~ CATCH2 ~~~~~~~~~~~~~~~~~~~~~~~~
FetchContent_Declare(
  Catch2
  GIT_REPOSITORY https://github.com/catchorg/Catch2.git
  GIT_TAG        v3.11.0
)

FetchContent_MakeAvailable(Catch2)

list(APPEND CMAKE_MODULE_PATH ${catch2_SOURCE_DIR}/extras)
include(CTest)
include(Catch)
# ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_COMPILER clang++)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_INCLUDE_WHAT_YOU_USE "include-what-you-use;-Xiwyu;--error")
set(CMAKE_CXX_CLANG_TIDY "clang-tidy;--use-color")
add_compile_options(
    -Wall
    -Wextra
    -Wpedantic
    -Wshadow
    -Wconversion
    -Wsign-conversion
    -Wnull-dereference
    -Wcast-align
    -Wstrict-aliasing
    -Wthread-safety
    -Werror)

add_executable(hello-world src/main.cc)

add_executable(hello-test src/test.cc)
target_link_libraries(hello-test PRIVATE Catch2::Catch2WithMain)
catch_discover_tests(hello-test)
