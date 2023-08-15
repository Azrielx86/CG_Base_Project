# File by Azrielx86 (Edgar Chalico)
cmake_minimum_required(VERSION 3.26)
project(ProjectName)
set(CMAKE_CXX_STANDARD 17)

# Requires GLEW, OpenGL and GLFW Packages on Linux
# On Arch Linux: pacman -S glew glfw
if (UNIX)
    add_definitions(-DLINUX_CMAKE)
    message(STATUS "Compiling on Linux or UNIX system.")
    # FIND PACKAGES FOR OpenGL
    find_package(OpenGL REQUIRED)
    if (OpenGL_FOUND)
        message(STATUS "OpenGL Found")
    endif ()

    # FIND PACKAGES FOR GLEW AND GLFW
    find_package(GLEW REQUIRED)
    if (GLEW_FOUND)
        message(STATUS "GLEW Found")
    endif ()

    find_package(glfw3 REQUIRED)
    if (glfw3_FOUND)
        message(STATUS "GLFW Found")
    endif ()
else () # Para Windows se requieren los archivos de OpenGL, GLFW y GLEW
        # proporcionados en el classroom de la clase.
    message("Compiling on Windows")
#    TODO
endif ()

add_executable(ProjectName main.cpp)
target_link_libraries(ProjectName glfw OpenGL::GL GLEW)
