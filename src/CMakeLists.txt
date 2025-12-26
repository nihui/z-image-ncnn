cmake_minimum_required(VERSION 3.10)
project(z-image-ncnn)

# set(ncnn_DIR "/home/nihui/osd/ncnn-nihui-fix/build/install/lib64/cmake/ncnn")
find_package(ncnn REQUIRED)

find_package(OpenCV REQUIRED core highgui imgproc)

set(CMAKE_CXX_STANDARD 17)

add_executable(z-image-ncnn
    bpe_tokenizer.cpp
    main.cpp
)

target_link_libraries(z-image-ncnn ncnn ${OpenCV_LIBS})
