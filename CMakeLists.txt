cmake_minimum_required(VERSION "3.7")

if(${CMAKE_VERSION} VERSION_LESS "3.12")
    cmake_policy(VERSION "${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION}")
endif()

project(QtAwesome VERSION 1.0 LANGUAGES CXX)

find_package(Qt5 COMPONENTS Core Gui Widgets REQUIRED)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

add_subdirectory(QtAwesome)
add_subdirectory(QtAwesomeSample)

install(EXPORT qtawesome-targets
    DESTINATION "share/cmake/targets"
    NAMESPACE "qtawesome::"
)

include(CMakePackageConfigHelpers)

write_basic_package_version_file(
    "${CMAKE_CURRENT_BINARY_DIR}/cmake/pkg/qtawesome-config-version.cmake"
    VERSION "${QTAWESOME_VERSION}"
    COMPATIBILITY SameMajorVersion
)

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/cmake/pkg/qtawesome-config.cmake.in"
               "${CMAKE_CURRENT_BINARY_DIR}/cmake/pkg/qtawesome-config.cmake" @ONLY)

install(
    FILES
        "${CMAKE_CURRENT_BINARY_DIR}/cmake/pkg/qtawesome-config.cmake"
        "${CMAKE_CURRENT_BINARY_DIR}/cmake/pkg/qtawesome-config-version.cmake"
    DESTINATION
        "share/cmake/qtawesome"
)
