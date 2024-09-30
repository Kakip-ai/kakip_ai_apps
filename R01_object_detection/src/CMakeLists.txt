cmake_minimum_required(VERSION 3.12)
project(object_detection_cpp)

set(CMAKE_CXX_STANDARD 17)

set(TVM_ROOT ../../3rdparty/rzv_drp-ai_tvm/tvm)
include_directories(${TVM_ROOT}/include)
include_directories(${TVM_ROOT}/3rdparty/dlpack/include)
include_directories(${TVM_ROOT}/3rdparty/dmlc-core/include)
include_directories(${TVM_ROOT}/3rdparty/compiler-rt)

set(OpenCVA_INCLUDE_DIRS /usr/include/renesas/opencv4)
set(OpenCVA_LIBS opencv_imgcodecs opencv_imgproc opencv_core opencv_highgui opencv_videoio)

set(TVM_RUNTIME_LIB /usr/lib/aarch64-linux-gnu/renesas/libtvm_runtime.so)
set(EXE_NAME object_detection)

file(GLOB SOURCE *.cpp *.h)
add_executable (${EXE_NAME}
${SOURCE}
)

target_link_directories(${EXE_NAME} PUBLIC /usr/lib/aarch64-linux-gnu/renesas)

target_link_libraries(${EXE_NAME} pthread)
target_link_libraries(${EXE_NAME} jpeg)
target_link_libraries(${EXE_NAME} mmngr mmngrbuf)
target_link_libraries(${EXE_NAME} ${OpenCVA_LIBS})

target_include_directories(${EXE_NAME} PUBLIC /usr/include/renesas ${OpenCVA_INCLUDE_DIRS})
target_link_libraries(${EXE_NAME} ${TVM_RUNTIME_LIB})

target_compile_definitions(${EXE_NAME} PRIVATE V2H)
