cmake_minimum_required(VERSION 3.0.0)
project(my_project_name VERSION 0.1.0)

include(CTest)
enable_testing()

find_package( OpenCV REQUIRED)
include_directories( ${OpenCV_INCLUDE_DIRS})
include_directories( include)
add_subdirectory(lib/glfw)
add_executable(my_project_name src/main.cpp src/glad.c)

list(APPEND EXTRA_LIBS
    "-lglfw3 -lGL -lGLU -lX11 -lpthread -lXrandr -lXi -ldl -lz"
)


target_link_libraries(my_project_name ${EXTRA_LIBS} )
target_link_libraries( my_project_name ${OpenCV_LIBS})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
