project(screensaver.matrixtrails)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(Kodi REQUIRED)
find_package(SOIL REQUIRED)

include(ExternalProject)

include_directories(${KODI_INCLUDE_DIR}/.. # Hack way with "/..", need bigger Kodi cmake rework to match right include ways
                    ${SOIL_INCLUDE_DIRS})

set(MATRIXTRAILS_SOURCES src/column.cpp
                         src/main.cpp
                         src/matrixtrails.cpp)

set(MATRIXTRAILS_HEADERS src/column.h
                         src/main.h
                         src/matrixtrails.h
                         src/Texture.h
                         src/timer.h
                         src/types.h)

set(DEPLIBS ${SOIL_LIBRARIES})

build_addon(screensaver.matrixtrails MATRIXTRAILS DEPLIBS)

include(CPack)
