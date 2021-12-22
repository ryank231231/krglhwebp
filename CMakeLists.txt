cmake_minimum_required (VERSION 3.10)
project (krglhwebp)

add_definitions(-DUNICODE -D_UNICODE)
add_definitions(-D_CRT_SECURE_NO_WARNINGS)

find_package(WebP CONFIG REQUIRED)

include_directories(tp_stub)

set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")

ADD_LIBRARY (krglhwebp SHARED src/dllmain.cpp tp_stub/tp_stub.cpp)
target_link_libraries(krglhwebp PRIVATE WebP::webp WebP::webpdemux WebP::libwebpmux WebP::webpdecoder)