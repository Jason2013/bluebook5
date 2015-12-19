cmake_minimum_required(VERSION 3.4)

# https://github.com/rpavlik/cmake-modules
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} C:/chenchang/dev/cmake-modules)
cmake_policy(SET CMP0026 OLD)
include(CreateLaunchers)

project(SuperBible5)

include_directories(C:/chenchang/dev/glew-1.13.0/include
    C:/chenchang/dev/freeglut-3.0.0/include
    GLTools/include
)

link_libraries(opengl32.lib
    C:/chenchang/dev/glew-1.13.0/build/cmake/bld/lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/libglew32$<$<CONFIG:Debug>:d>.lib
    C:/chenchang/dev/freeglut-3.0.0/bld/lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/freeglut$<$<CONFIG:Debug>:_staticd>.lib
)

add_library(gltools STATIC
    GLTools/src/GLShaderManager.cpp
    GLTools/src/GLTools.cpp
    GLTools/src/GLTriangleBatch.cpp
    GLTools/src/math3d.cpp
    GLTools/include/GLBatch.h
    GLTools/include/GLBatchBase.h
    GLTools/include/GLFrame.h
    GLTools/include/GLFrustum.h
    GLTools/include/GLMatrixStack.h
    GLTools/include/GLShaderManager.h
    GLTools/include/GLTools.h
    GLTools/include/GLTriangleBatch.h
    GLTools/include/Stopwatch.h
    GLTools/include/math3d.h
    GLTools/src/GLBatch.cpp
)

set_target_properties(gltools PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
    ARCHIVE_OUTPUT_DIRECTORY lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>
)

add_executable(Anisotropic
    Chapter05/Anisotropic/Tunnel.cpp
)

set_target_properties(Anisotropic PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Anisotropic
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Anisotropic gltools)

create_target_launcher(Anisotropic WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter05/Anisotropic/")

add_executable(Pyramid
    Chapter05/Pyramid/Pyramid.cpp
)

set_target_properties(Pyramid PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Pyramid
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Pyramid gltools)

create_target_launcher(Pyramid WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter05/Pyramid/")

add_executable(SphereWorld
    Chapter05/SphereWorld/SphereWorld.cpp
)

set_target_properties(SphereWorld PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereWorld
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereWorld gltools)

create_target_launcher(SphereWorld WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter05/SphereWorld/")

add_executable(Tunnel
    Chapter05/Tunnel/Tunnel.cpp
)

set_target_properties(Tunnel PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Tunnel
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Tunnel gltools)

create_target_launcher(Tunnel WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter05/Tunnel/")

add_executable(CubeMapped
    Chapter07/CubeMapped/Cubemap.cpp
)

set_target_properties(CubeMapped PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(CubeMapped
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(CubeMapped gltools)

create_target_launcher(CubeMapped WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/CubeMapped/")

add_executable(TextureRect
    Chapter07/TextureRect/SphereWorld.cpp
)

set_target_properties(TextureRect PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(TextureRect
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(TextureRect gltools)

create_target_launcher(TextureRect WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/TextureRect/")

add_executable(explode
    Chapter11/Convolution/explode.h
    Chapter11/Convolution/explode.cpp
    Chapter11/Convolution/GLMain.cpp
)

set_target_properties(explode PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
    LINK_FLAGS "/SUBSYSTEM:WINDOWS"
)

target_link_libraries(explode
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(explode gltools)

create_target_launcher(explode WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/Convolution/")
