cmake_minimum_required(VERSION 3.4)

# https://github.com/rpavlik/cmake-modules
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} C:/chenchang/dev/cmake-modules)
cmake_policy(SET CMP0026 OLD)
include(CreateLaunchers)

project(SuperBible5)

include_directories(C:/chenchang/dev/glfw-3.1.2/include
#    C:/chenchang/dev/glew-1.13.0/include
    C:/chenchang/dev/freeglut-3.0.0/include
    common
    GLTools/include
)

link_libraries(opengl32.lib
#    C:/chenchang/dev/glfw-3.1.2/bld/src/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/glfw3.lib
#    C:/chenchang/dev/glew-1.13.0/build/cmake/bld/lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/libglew32$<$<CONFIG:Debug>:d>.lib
    C:/chenchang/dev/freeglut-3.0.0/bld/lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/freeglut$<$<CONFIG:Debug>:_staticd>.lib
)

add_library(gltools STATIC
    GLTools/src/GLShaderManager.cpp
    GLTools/src/GLTools.cpp
    GLTools/src/GLTriangleBatch.cpp
    GLTools/src/glew.c
    GLTools/src/math3d.cpp
    GLTools/include/GLBatch.h
    GLTools/include/GLBatchBase.h
    GLTools/include/GLFrame.h
    GLTools/include/GLFrustum.h
    GLTools/include/GLMatrixStack.h
    GLTools/include/GLShaderManager.h
    GLTools/include/GLTools.h
    GLTools/include/GLTriangleBatch.h
#    GLTools/include/GLee.h
    GLTools/include/Stopwatch.h
    GLTools/include/math3d.h
    GLTools/src/GLBatch.cpp
)
set_target_properties(gltools PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

#SET_TARGET_PROPERTIES(gltools PROPERTIES LINKER_LANGUAGE CXX)


add_executable(Pyramid
    Chapter05/Pyramid/Pyramid.cpp
)

set_target_properties(Pyramid PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Pyramid
    ${CMAKE_CURRENT_SOURCE_DIR}/bld/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools.lib
)

add_dependencies(Pyramid gltools)

create_target_launcher(Pyramid WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter05/Pyramid/")
