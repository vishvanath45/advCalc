cmake_minimum_required(VERSION 3.7)
project(advCalc)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/modules")

if (EXISTS "${ROOT}/usr/local/opt/readline/include")
    include_directories(${ROOT}/usr/local/opt/readline/include)
    message(STATUS "Mac OS users, Found GNU Readline headers")
else()
    message(STATUS "Mac OS users, Unable to find GNU Readline headers")
    message(STATUS "Others don't care")
endif()

# message(STATUS "some ${CMAKE_SOURCE_DIR}")
# message(STATUS "some ${PROJECT_SOURCE_DIR}")

set(LIB_ADVCALC advCalc)
set(LIB_SRC src/calcError.cpp src/str.cpp src/calcOptr.cpp)
set(LIB_HPP  src/calcError.hpp src/str.hpp
    src/calcOptr.hpp src/calcStack.hpp
    src/common.hpp)

add_library(${LIB_ADVCALC} ${LIB_SRC} ${LIB_HPP})

set(LIBS ${LIB_ADVCALC})

add_subdirectory(src/)
add_subdirectory(src/calc_ui_qt)

