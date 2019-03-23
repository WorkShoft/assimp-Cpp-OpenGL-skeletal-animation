cmake_minimum_required(VERSION 3.6)   # CMake version check
project(assimp_cpp_opengl_skeletal_animation)  

set(CMAKE_CXX_STANDARD 11)            # Enable c++11 standard
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR})
  
file(GLOB HEADERS
  *.h
  *.cpp
  )

set(SOURCE_FILES main.cpp )


add_executable(main ${SOURCE_FILES} ${HEADERS})


set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)
target_link_libraries(main Threads::Threads)


#OPENGL
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR})
target_link_libraries(main ${OPENGL_gl_LIBRARY})

#GLFW
find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)
include_directories(${GLFW_INCLUDE_DIRS})
target_link_libraries(main ${GLFW_LIBRARIES})

#SDL2

PKG_SEARCH_MODULE(SDL2 REQUIRED sdl2)
PKG_SEARCH_MODULE(SDL2IMAGE REQUIRED SDL2_image>=2.0.0)
INCLUDE_DIRECTORIES(${SDL2_INCLUDE_DIRS} ${SDL2IMAGE_INCLUDE_DIRS})
TARGET_LINK_LIBRARIES(main ${SDL2_LIBRARIES} ${SDL2IMAGE_LIBRARIES})

#SDL2_MIXER
find_package(SDL2_MIXER REQUIRED
pkg_search_module(SDL2_MIXER REQUIRED))
include_directories(${SDL2MIXER_INCLUDE_DIR})
set(LIBS ${LIBS} ${SDL2MIXER_LIBRARY})
target_link_libraries(main ${LIBS})

#GLUT
find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIRS})
target_link_libraries(main ${GLUT_LIBRARIES})

#ASSIMP
find_package(ASSIMP REQUIRED)
include_directories(${ASSIMP_INCLUDE_DIRS})
target_link_libraries(main ${ASSIMP_LIBRARIES})

#DEVIL
find_package(DevIL REQUIRED)
include_directories(${DEVIL_INCLUDE_DIRS})
target_link_libraries(main ${IL_LIBRARIES} ${ILU_LIBRARIES} ${ILUT_LIBRARIES})

#GLEW
find_package(GLEW REQUIRED)
if (GLEW_FOUND)
    include_directories(${GLEW_INCLUDE_DIRS})
    target_link_libraries(main ${GLEW_LIBRARIES})
  endif()
  
#GLM
include_directories(main ${GLM_INCLUDE_DIRS})

#FREETYPE
find_package(Freetype REQUIRED)
include_directories(${FREETYPE_INCLUDE_DIRS})
target_link_libraries(main ${FREETYPE_LIBRARIES})
 







