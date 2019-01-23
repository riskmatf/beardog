cmake_minimum_required(VERSION 3.10)

project(beardog)
include_directories(include/)
include_directories(thirdparty/include/)
file(GLOB SOURCES "src/*.cpp")

# ----------------------------------------------------------------------------------------------------------------------
# Conan package manager
# ----------------------------------------------------------------------------------------------------------------------
# Run this to generate conanbuildinfo.cmake
# conan install . -s build_type=Debug --install-folder=cmake-build-debug
# Same for release
# conan install . -s build_type=Release --install-folder=cmake-build-release
# ----------------------------------------------------------------------------------------------------------------------
if (EXISTS ${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
    include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
    conan_basic_setup()
else ()
    message(WARNING "The file conanbuildinfo.cmake doesn't exist, you have to run conan install first")
endif ()
# ----------------------------------------------------------------------------------------------------------------------

# Set executable.
add_executable(${PROJECT_NAME} ${SOURCES})

# Link conan libraries
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})

# ----------------------------------------------------------------------------------------------------------------------
# Choosing C++ standard.
# ----------------------------------------------------------------------------------------------------------------------
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 14)
if (UNIX AND NOT APPLE)
    set(CMAKE_CXX_STANDARD_LIBRARIES "-std=c++14")
endif()
# ----------------------------------------------------------------------------------------------------------------------

