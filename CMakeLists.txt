cmake_minimum_required(VERSION 3.10)
project(myserver)

set(CMAKE_CXX_STANDARD 17)

find_package(Boost)
IF (Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIR})
endif()

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -lpqxx -lpq")

set(PQXX /usr/local/include/pqxx)

find_library(PQXX_LIB pqxx)
find_library(PQ_LIB pq)

file(GLOB_RECURSE SOURCE_FILES "src/*.cpp")


add_executable(myserver ${SOURCE_FILES})




TARGET_LINK_LIBRARIES(myserver  ${PQXX_LIB} ${PQ_LIB})
