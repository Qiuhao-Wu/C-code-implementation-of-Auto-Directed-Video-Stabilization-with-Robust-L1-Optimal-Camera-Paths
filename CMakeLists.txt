cmake_minimum_required(VERSION 2.8.12)
project(videoStab_L1)


include_directories(lpsolve)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories("D:\\videoStabL1\\lpsolve")

set(OpenCV_DIR C:\\Program Files (x86)\\opencv\\opencv\\opencv\\build)
find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

set(LPSOLVE_LIBRARIES D:\\videoStabL1\\lpsolve\\lpsolve55.lib)

set(LPSOLVE_DLL D:\\videoStabL1\\lpsolve\\lpsolve55.dll)

add_executable(videoStab videostab.cpp)

#target_link_libraries(VideoStablization cvplot)
TARGET_LINK_LIBRARIES(videoStab PRIVATE ${LPSOLVE_LIBRARIES})
TARGET_LINK_LIBRARIES(videoStab PUBLIC ${OpenCV_LIBS})

configure_file(${LPSOLVE_DLL} ${CMAKE_BINARY_DIR}/lpsolve55.dll COPYONLY)
set_target_properties(videoStab PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})