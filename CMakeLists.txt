cmake_minimum_required(VERSION 3.10)

include(CMakePrintHelpers)



file(GLOB SOURCES *.h *.cpp )
cmake_print_variables(SOURCES)
get_filename_component(full_path_test_cpp ${CMAKE_CURRENT_SOURCE_DIR}/test.cpp ABSOLUTE)
list(REMOVE_ITEM SOURCES "${full_path_test_cpp}")
get_filename_component(full_path_test_cpp ${CMAKE_CURRENT_SOURCE_DIR}/cpp_out.cpp ABSOLUTE)
list(REMOVE_ITEM SOURCES "${full_path_test_cpp}")
find_package(OpenCV REQUIRED)
cmake_print_variables(${OpenCV_INCLUDE_DIRS})
include_directories(${OpenCV_INCLUDE_DIRS})
add_library(patchmatch_inpaint SHARED ${SOURCES})
target_link_libraries(patchmatch_inpaint ${OpenCV_LIBRARIES})