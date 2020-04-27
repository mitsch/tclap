cmake_minimum_required(VERSION 3.7)

project(TCLAP VERSION 1.4.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 98)
set(CMAKE_CXX_STANDARD_REQUIRED True)
add_definitions(-DHAVE_TCLAP_CONFIG_H)

enable_testing()
include(CTest)

include(CheckCXXSourceCompiles)
check_cxx_source_compiles("#include <strstream>
int main() { std::istrstream iss; }" TCLAP_HAVE_STRSTREAM)

check_cxx_source_compiles("#include <sstream>
int main() { std::istringstream iss; }" TCLAP_HAVE_SSTREAM)

configure_file(config.h.in tclap/TCLAPConfig.h)

add_library(TCLAP INTERFACE)
target_include_directories(TCLAP INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:$include>)
install(TARGETS TCLAP EXPORT tclapTargets DESTINATION include)
install(FILES "${PROJECT_BINARY_DIR}/tclap/TCLAPConfig.h"
  DESTINATION include/tclap
  )
install(EXPORT tclapTargets DESTINATION lib/cmake/tclap FILE tclapTargets.cmake)
install(CMakePackageConfigHelpers)
write_basic_package_version_file(tclapConfigVersion.cmake
        VERSION ${PROJECT_VERSION}
        COMPATIBILITY SameMajorVersion)
install(FILES tclapConfig.cmake ${CMAKE_CURRENT_BINARY_DIR}/tclapConfigVersion.cmake DESTINATION lib/cmake/tclap)


add_subdirectory(docs)
add_subdirectory(examples)
add_subdirectory(tests)
add_subdirectory(include/tclap)
