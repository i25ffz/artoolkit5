#
# Copyright (C) The Android Open Source Project
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

cmake_minimum_required(VERSION 3.4.1)

include(AndroidNdkModules)
android_ndk_import_module_cpufeatures()

# configure import libs
set(AR_ROOT_DIR ${CMAKE_SOURCE_DIR}/../../../../../..)

# add static librarys
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/AR ar)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/AR2 ar2)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/ARICP aricp)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/Gl argsub_es)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/KPM kpm)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/Util util)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/Eden eden)
add_subdirectory(${AR_ROOT_DIR}/lib/SRC/Video arvideo)

# add jpeg static library
add_library(jpeg STATIC IMPORTED)
set_target_properties(jpeg PROPERTIES IMPORTED_LOCATION
    ${AR_ROOT_DIR}/android/obj/local/${ANDROID_ABI}/libjpeg.a)

# add curl static library
add_library(curl STATIC IMPORTED)
set_target_properties(curl PROPERTIES IMPORTED_LOCATION
    ${AR_ROOT_DIR}/android/jni/curl/libs/${ANDROID_ABI}/libcurl.a)

# build application's shared lib
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -frtti -fexceptions -DDEBUG")

add_library(nftSimpleNative SHARED
            ARMarkerNFT.c trackingSub.c nftSimple.cpp)

target_include_directories(nftSimpleNative PRIVATE
                           ${AR_ROOT_DIR}/include)

target_link_libraries(nftSimpleNative
                      ar2
                      argsub_es
                      kpm
                      util
                      eden
                      ar
                      aricp
                      arvideo
                      jpeg
                      curl
                      cpufeatures
                      log
                      GLESv1_CM
                      z)
