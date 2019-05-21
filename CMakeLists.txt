cmake_minimum_required(VERSION 2.8.3)
project(doctest_catkin)

catkin_package()

include(ExternalProject)

file(MAKE_DIRECTORY ${CATKIN_DEVEL_PREFIX}/include)
ExternalProject_Add(doctest_src
  GIT_REPOSITORY https://github.com/onqtam/doctest
  GIT_TAG master
  UPDATE_COMMAND ""
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX:PATH=${CATKIN_DEVEL_PREFIX}
)

install(DIRECTORY ${CATKIN_DEVEL_PREFIX}/include/doctest
        DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}
        FILES_MATCHING PATTERN "*.h")
install(DIRECTORY ${CATKIN_DEVEL_PREFIX}/lib/
        DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
        FILES_MATCHING PATTERN "libdoctest*")
