cmake_minimum_required(VERSION 2.8.3)
project(qpOASES)

find_package(catkin REQUIRED)

set(CMAKE_MODULE_PATH cmake)
include(ExternalProject)


ExternalProject_Add(
   qpOASES
   SVN_REPOSITORY https://projects.coin-or.org/svn/qpOASES/stable/3.2
   CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CATKIN_DEVEL_PREFIX}
   UPDATE_COMMAND sed -i "s/-DLINUX/-DLINUX -fPIC/g" CMakeLists.txt
   SOURCE_DIR ${PROJECT_SOURCE_DIR}/qpOASES_svn
)

catkin_package(DEPENDS qpOASES)

install(
  DIRECTORY ${PROJECT_SOURCE_DIR}/qpOASES_svn/include
  DESTINATION ${CMAKE_INSTALL_PREFIX}
  PATTERN ".svn" EXCLUDE
  )
