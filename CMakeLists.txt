cmake_minimum_required(VERSION 3.0.0)
project(helloworld_mpi VERSION 0.1.0 LANGUAGES C CXX)

include(CTest)
enable_testing()

add_executable(helloworld_mpi main.cpp)

find_package(MPI REQUIRED)
add_definitions(-DOMPI_SKIP_MPICXX)
include_directories(SYSTEM ${MPI_INCLUDE_PATH})
target_link_libraries(helloworld_mpi ${MPI_C_LIBRARIES})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
