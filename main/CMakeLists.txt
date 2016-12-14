cmake_minimum_required(VERSION 2.8)

project(myapp)

INCLUDE_DIRECTORIES(../_install/include)
LINK_DIRECTORIES(../_install/lib/)

add_executable(myapp main.cpp)
target_link_libraries(myapp hello)

install(TARGETS myapp DESTINATION bin)
