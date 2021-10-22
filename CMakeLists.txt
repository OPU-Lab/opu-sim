cmake_minimum_required(VERSION 3.1.0)
project (simulator)

set(CMAKE_CXX_FLAGS  "--std=c++11 -g")

include_directories("./")

set(SOURCES src/driver.cc src/instruction.cc src/accelerator.cc src/vmem.cc src/profiler.cc)

add_executable(simulator ${SOURCES})

target_link_libraries(simulator "-lglog")
find_path(GLOG_INCLUDE_DIR glog/logging.h)
target_include_directories(simulator PUBLIC ${GLOG_INCLUDE_DIR})


#add_executable(txt2bin util/txt2bin.cpp)


include_directories(3rdparty/json/single_include)
set(SOURCES1 src/driver_json.cc src/instruction.cc src/accelerator.cc src/vmem.cc src/profiler.cc)
add_executable(sim-json ${SOURCES1})
target_link_libraries(sim-json "-lglog")
target_include_directories(sim-json PUBLIC ${GLOG_INCLUDE_DIR})
