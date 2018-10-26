cmake_minimum_required(VERSION 3.10)
project(Rectangle)

if(CMAKE_COMPILER_IS_GNUCXX)
    set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS} -lglfw -lGL -lX11 -lpthread -lXrandr -lXi -ldl")
    message(STATUS "optional:-std=c++11")   
endif(CMAKE_COMPILER_IS_GNUCXX)

#include_directories("${PROJECT_SOURCE_DIR}/rectangle")
find_package(OpenGL REQUIRED)

include_directories(${GLFW_INCLUDE_DIR})


add_executable(rectangle rectangle.cpp)
target_link_libraries(rectangle ${DEPENDENCIES})

