cmake_minimum_required(VERSION 2.8)

project(hello_project)

add_library(hello SHARED hello.cpp)

install(TARGETS hello DESTINATION lib)
install(FILES hello.h DESTINATION include)
