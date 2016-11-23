cmake_minimum_required(VERSION 3.4.1)

add_library(native-activity SHARED
        src/main/cpp/main.cpp )

add_library(app-glue STATIC
        ${ANDROID_NDK}/sources/android/native_app_glue/android_native_app_glue.c )

target_include_directories(native-activity PRIVATE
        ${ANDROID_NDK}/sources/android/native_app_glue )

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

target_link_libraries(native-activity android app-glue EGL GLESv1_CM log)
