cmake_minimum_required(VERSION 3.10)
project(z-image-ncnn)

set(NCNN_BUILD_TESTS OFF)
set(NCNN_BUILD_BENCHMARK OFF)
set(NCNN_BUILD_TOOLS OFF)
set(NCNN_BUILD_EXAMPLES OFF)
add_subdirectory(ncnn)

find_package(OpenCV REQUIRED)
message("OpenCV_DIR: ${OpenCV_DIR}")

set(CMAKE_CXX_STANDARD 17)

add_executable(z-image-ncnn
    bpe_tokenizer.cpp
    main.cpp
)

target_link_libraries(z-image-ncnn ncnn ${OpenCV_LIBS})
