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
    C:/chenchang/dev/freeglut-3.0.0/bld/lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/freeglut_static$<$<CONFIG:Debug>:d>.lib
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

add_executable(Block
    Chapter01/Block/Block.cpp
)

set_target_properties(Block PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Block
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Block gltools)

create_target_launcher(Block WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter01/Block/")

add_executable(Bounce
    Chapter02/Bounce/Bounce.cpp
)

set_target_properties(Bounce PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Bounce
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Bounce gltools)

create_target_launcher(Bounce WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter02/Bounce/")

add_executable(Move
    Chapter02/Move/Move.cpp
)

set_target_properties(Move PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Move
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Move gltools)

create_target_launcher(Move WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter02/Move/")

add_executable(Triangle
    Chapter02/Triangle/Triangle.cpp
)

set_target_properties(Triangle PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Triangle
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Triangle gltools)

create_target_launcher(Triangle WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter02/Triangle/")

add_executable(Blending
    Chapter03/Blending/Blending.cpp
)

set_target_properties(Blending PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Blending
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Blending gltools)

create_target_launcher(Blending WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter03/Blending/")

add_executable(GeoTest
    Chapter03/GeoTest/GeoTest.cpp
)

set_target_properties(GeoTest PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(GeoTest
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(GeoTest gltools)

create_target_launcher(GeoTest WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter03/GeoTest/")

add_executable(Primitives
    Chapter03/Primitives/Primitives.cpp
)

set_target_properties(Primitives PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Primitives
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Primitives gltools)

create_target_launcher(Primitives WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter03/Primitives/")

add_executable(Scissor
    Chapter03/Scissor/Scissor.cpp
)

set_target_properties(Scissor PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Scissor
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Scissor gltools)

create_target_launcher(Scissor WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter03/Scissor/")

add_executable(Smoother
    Chapter03/Smoother/Smoother.cpp
)

set_target_properties(Smoother PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Smoother
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Smoother gltools)

create_target_launcher(Smoother WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter03/Smoother/")

add_executable(ModelViewProjection
    Chapter04/ModelViewProjection/ModelViewProjection.cpp
)

set_target_properties(ModelViewProjection PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(ModelViewProjection
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(ModelViewProjection gltools)

create_target_launcher(ModelViewProjection WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/ModelViewProjection/")

add_executable(Move_ch04
    Chapter04/Move/Move.cpp
)

set_target_properties(Move_ch04 PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Move_ch04
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Move_ch04 gltools)

create_target_launcher(Move_ch04 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/Move/")

add_executable(Objects
    Chapter04/Objects/Objects.cpp
)

set_target_properties(Objects PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Objects
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Objects gltools)

create_target_launcher(Objects WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/Objects/")

add_executable(OrthoGraphic
    Chapter04/OrthoGraphic/OrthoGraphic.cpp
)

set_target_properties(OrthoGraphic PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(OrthoGraphic
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(OrthoGraphic gltools)

create_target_launcher(OrthoGraphic WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/OrthoGraphic/")

add_executable(Perspective
    Chapter04/Perspective/Perspective.cpp
)

set_target_properties(Perspective PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Perspective
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Perspective gltools)

create_target_launcher(Perspective WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/Perspective/")

add_executable(SphereWorld
    Chapter04/SphereWorld/SphereWorld.cpp
)

set_target_properties(SphereWorld PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereWorld
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereWorld gltools)

create_target_launcher(SphereWorld WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/SphereWorld/")

add_executable(SphereWorld2
    Chapter04/SphereWorld2/SphereWorld2.cpp
)

set_target_properties(SphereWorld2 PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereWorld2
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereWorld2 gltools)

create_target_launcher(SphereWorld2 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/SphereWorld2/")

add_executable(SphereWorld3
    Chapter04/SphereWorld3/SphereWorld3.cpp
)

set_target_properties(SphereWorld3 PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereWorld3
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereWorld3 gltools)

create_target_launcher(SphereWorld3 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/SphereWorld3/")

add_executable(SphereWorld4
    Chapter04/SphereWorld4/SphereWorld4.cpp
)

set_target_properties(SphereWorld4 PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereWorld4
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereWorld4 gltools)

create_target_launcher(SphereWorld4 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter04/SphereWorld4/")

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

add_executable(SphereWorld_ch05
    Chapter05/SphereWorld/SphereWorld.cpp
)

set_target_properties(SphereWorld_ch05 PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereWorld_ch05
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereWorld_ch05 gltools)

create_target_launcher(SphereWorld_ch05 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter05/SphereWorld/")

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

add_executable(MultiTexture
    Chapter07/MultiTexture/MultiTexture.cpp
)

set_target_properties(MultiTexture PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(MultiTexture
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(MultiTexture gltools)

create_target_launcher(MultiTexture WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/MultiTexture/")

add_executable(NormalMapped
    Chapter07/NormalMapped/NormalMapped.cpp
)

set_target_properties(NormalMapped PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(NormalMapped
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(NormalMapped gltools)

create_target_launcher(NormalMapped WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/NormalMapped/")

add_executable(PointSprites
    Chapter07/PointSprites/PointSprites.cpp
)

set_target_properties(PointSprites PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(PointSprites
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(PointSprites gltools)

create_target_launcher(PointSprites WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/PointSprites/")

add_executable(SphereMapped
    Chapter07/SphereMapped/SphereMapped.cpp
)

set_target_properties(SphereMapped PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(SphereMapped
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(SphereMapped gltools)

create_target_launcher(SphereMapped WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/SphereMapped/")

add_executable(TextureArrays
    Chapter07/TextureArrays/TextureArrays.cpp
)

set_target_properties(TextureArrays PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(TextureArrays
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(TextureArrays gltools)

create_target_launcher(TextureArrays WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter07/TextureArrays/")

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

add_executable(fbo_drawbuffers
    Chapter08/fbo_drawbuffers/fbo_drawbuffers.cpp
    Models/Ninja/sbm.cpp
)

target_include_directories(fbo_drawbuffers PUBLIC
    Models/Ninja
)

set_target_properties(fbo_drawbuffers PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(fbo_drawbuffers
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(fbo_drawbuffers gltools)

create_target_launcher(fbo_drawbuffers WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter08/fbo_drawbuffers/")

add_executable(fbo_textures
    Chapter08/fbo_textures/fbo_textures.cpp
)

set_target_properties(fbo_textures PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(fbo_textures
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(fbo_textures gltools)

create_target_launcher(fbo_textures WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter08/fbo_textures/")

add_executable(pix_buffs
    Chapter08/pix_buffs/pix_buffs.cpp
)

set_target_properties(pix_buffs PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(pix_buffs
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(pix_buffs gltools)

create_target_launcher(pix_buffs WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter08/pix_buffs/")

add_executable(oit
    Chapter10/oit/oit.cpp
)

set_target_properties(oit PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(oit
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(oit gltools)

create_target_launcher(oit WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter10/oit/")

add_executable(Convolution
    Chapter11/Convolution/explode.cpp
    Chapter11/Convolution/GLMain.cpp
)

set_target_properties(Convolution PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
    LINK_FLAGS "/SUBSYSTEM:WINDOWS"
)

target_link_libraries(Convolution
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Convolution gltools)

create_target_launcher(Convolution WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/Convolution/")

add_executable(GSCulling
    Chapter11/GSCulling/GSCulling.cpp
)

set_target_properties(GSCulling PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(GSCulling
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(GSCulling gltools)

create_target_launcher(GSCulling WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/GSCulling/")

add_executable(GSExplode
    Chapter11/GSExplode/GSExplode.cpp
)

set_target_properties(GSExplode PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(GSExplode
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(GSExplode gltools)

create_target_launcher(GSExplode WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/GSExplode/")

add_executable(GSNormals
    Chapter11/GSNormals/GSNormals.cpp
)

set_target_properties(GSNormals PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(GSNormals
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(GSNormals gltools)

create_target_launcher(GSNormals WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/GSNormals/")

add_executable(GSTessellate
    Chapter11/GSTessellate/GSTessellate.cpp
)

set_target_properties(GSTessellate PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(GSTessellate
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(GSTessellate gltools)

create_target_launcher(GSTessellate WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/GSTessellate/")

add_executable(Julia
    Chapter11/Julia/Julia.cpp
)

set_target_properties(Julia PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Julia
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Julia gltools)

create_target_launcher(Julia WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/Julia/")

add_executable(Perspective_ch11
    Chapter11/Perspective/Perspective.cpp
)

set_target_properties(Perspective_ch11 PROPERTIES
    COMPILE_DEFINITIONS GLEW_STATIC
)

target_link_libraries(Perspective_ch11
    lib/$<$<CONFIG:Debug>:Debug>$<$<NOT:$<CONFIG:Debug>>:Release>/gltools
)

add_dependencies(Perspective_ch11 gltools)

create_target_launcher(Perspective_ch11 WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/Chapter11/Perspective/")

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
