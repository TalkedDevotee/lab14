cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_STANDARD 11)

include(cmake/HunterGate.cmake)
include(CPack)

HunterGate(URL "https://github.com/TalkedDevotee/hunter/archive/v0.19.137.1.tar.gz" SHA1 "c73c56fb3af2b888652d1b3cab682cc08a55f972")

project(builder)

hunter_add_package(Boost COMPONENTS program_options system filesystem)
find_package(Boost CONFIG REQUIRED program_options system filesystem)

add_executable(builder ${CMAKE_CURRENT_SOURCE_DIR}/builder.cpp)
target_link_libraries(builder Boost::program_options Boost::system Boost::filesystem)

install(TARGETS builder RUNTIME DESTINATION bin)
