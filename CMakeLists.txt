cmake_minimum_required(VERSION 3.10)
project("PDF_sample" VERSION 0.1)

set(CMAKE_CXX_STANDARD 17)
# podofo disk
# set(NLOHMANN_LIB "C:/develop/nlohmann_json")
# set(NILS_LIB ${CMAKE_SOURCE_DIR}/nlohmann_json/include)
set(PODOFO_BUILD_LIB_ONLY TRUE CACHE BOOL "" FORCE)
set(PODOFO_BUILD_STATIC TRUE CACHE BOOL "" FORCE)

set(podofo_LIB "C:/develop/PDFViewerQT-main")
set(podofo_LIBS ${CMAKE_SOURCE_DIR}/podofo)
# set(CMAKE_PREFIX_PATH "C:\\Qt\\6.8.0\\mingw_64\\lib\\cmake")
include(FetchContent)
FetchContent_Declare(podofo URL ${podofo_LIB})
FetchContent_MakeAvailable(podofo)

# net content
# include(FetchContent)
# FetchContent_Declare(podofo URL https://github.com/podofo/podofo.git)
# FetchContent_MakeAvailable(podofo)

add_subdirectory(podofo)
target_link_libraries(PDF_sample podofo::podofo)

# find_package(Qt6 COMPONENTS Core Widgets REQUIRED)
find_package(podofo CONFIG REQUIRED)
set(MY_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/include)
# enable_testing()#true

add_executable(PDF_sample src/main.cpp)
target_include_directories(PDF_sample PUBLIC ${MY_INCLUDE_DIR})

