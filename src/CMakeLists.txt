cmake_minimum_required(VERSION 2.8.12)
set(CMAKE_CXX_STANDARD 14)
project(monogenic_phase_analysis)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
set(ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
set(EXT_PROJECTS_DIR ${CMAKE_SOURCE_DIR}/external)


find_package(ITK COMPONENTS IsotropicWavelets ITKIOImageBase ITKIOTIFF ITKIOPNG ITKIOJPEG REQUIRED)
include_directories(${ITK_INCLUDE_DIRS})
include(${ITK_USE_FILE})
message(status "** ITK Libraries:  ${ITK_LIBRARIES}")
message(status "** ITK Includes:  ${ITK_INCLUDE_DIRS}")

# find_package(Boost COMPONENTS
#         system filesystem
#         program_options
#         REQUIRED )
# include_directories(SYSTEM ${Boost_INCLUDE_DIRS})

# For proper linking in install tree.
add_executable(monogenic_phase_analysis ${CMAKE_CURRENT_SOURCE_DIR}/MonogenicPhaseAnalysis.cpp)
target_link_libraries(monogenic_phase_analysis ${ITK_LIBRARIES})
