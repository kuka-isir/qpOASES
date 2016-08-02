cmake_minimum_required(VERSION 2.8.3)
project(qpOASES CXX)
set(qpOASES_VERSION "3.2.0")

set(CMAKE_MODULE_PATH cmake)
include(ExternalProject)

find_package(catkin REQUIRED)

ExternalProject_Add(
   qpOASES
   SVN_REPOSITORY https://projects.coin-or.org/svn/qpOASES/stable/3.2
   CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CATKIN_DEVEL_PREFIX}
   UPDATE_COMMAND sed -i "s/-DLINUX/-DLINUX -fPIC/g" CMakeLists.txt
   SOURCE_DIR ${PROJECT_SOURCE_DIR}/qpOASES_svn
)

catkin_package(
    INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/qpOASES_svn/include
    LIBRARIES qpOASES
)

install(
    DIRECTORY ${PROJECT_SOURCE_DIR}/qpOASES_svn/include
    DESTINATION ${CMAKE_INSTALL_PREFIX}
    PATTERN ".svn" EXCLUDE
)
install(
    FILES ${CATKIN_DEVEL_PREFIX}/lib/${CMAKE_STATIC_LIBRARY_PREFIX}${PROJECT_NAME}${CMAKE_STATIC_LIBRARY_SUFFIX}
    DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)
