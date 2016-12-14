cmake_minimum_required(VERSION 2.8)
include(ExternalProject)
project(myapp)

set(hello_install_dir ${CMAKE_CURRENT_BINARY_DIR}/../_install)
ExternalProject_Add(hello_project
  GIT_REPOSITORY /home/xxx/git-test/remote/plugin.git
  PREFIX ${CMAKE_CURRENT_BINARY_DIR}/hello
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${hello_install_dir}
)

ExternalProject_Get_Property(hello_project install_dir)


add_library(hello SHARED IMPORTED)
set_property(TARGET hello PROPERTY IMPORTED_LOCATION ${hello_install_dir}/lib/libhello.so)
add_dependencies(hello hello_project)

include_directories(${hello_install_dir}/include/)



add_executable(myapp main.cpp)
target_link_libraries(myapp hello)

install(TARGETS myapp DESTINATION bin)
