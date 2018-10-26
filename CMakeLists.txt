cmake_minimum_required(VERSION 3.10)
project(LearningOpengl)

#if(CMAKE_COMPILER_IS_GNUCXX)
#    set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS} -lglfw -lGL -lX11 -lpthread -lXrandr -lXi -ldl")
#    message(STATUS "optional:-std=c++11")   
#endif(CMAKE_COMPILER_IS_GNUCXX)

option (BUILD_RECTANGLE "To build the rectangle" ON)

add_subdirectory(Glad)

set(DEPENDENCIES Glad)

# Find glfw header
find_path(GLFW_INCLUDE_DIR NAMES GLFW/glfw3.h
    PATHS /usr/X11R6/include
          /usr/include/X11
          /opt/graphics/OpenGL/include
          /opt/graphics/OpenGL/contrib/libglfw
          /usr/local/include
          /usr/include/GL
          /usr/include
)
# Find glfw library
find_library(GLFW_LIBRARIES NAMES glfw glfw3
        PATHS /usr/lib64
              /usr/lib
              /usr/lib/${CMAKE_LIBRARY_ARCHITECTURE}
              /usr/local/lib64
              /usr/local/lib
              /usr/local/lib/${CMAKE_LIBRARY_ARCHITECTURE}
              /usr/X11R6/lib
)

list(APPEND DEPENDENCIES m ${GLFW_LIBRARIES})

if (BUILD_RECTANGLE)
    add_subdirectory(rectangle)
endif()
