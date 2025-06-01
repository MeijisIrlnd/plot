cmake_minimum_required(VERSION 3.24)
project(plot VERSION 1.0.0)

add_library(plot INTERFACE)
add_library(signalsmith::plot ALIAS plot)
target_include_directories(plot INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)

if (${SIGNALSMITH_PLOT_EXAMPLES})
    add_executable(plot-examples ${CMAKE_CURRENT_SOURCE_DIR}/doc/examples.cpp)
    target_link_libraries(plot-examples PRIVATE plot)
endif ()