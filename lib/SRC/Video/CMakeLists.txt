set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti -DHAVE_ARM_NEON=1")

file(GLOB VIDEO_SRC_LIST *.c)

add_library(arvideo STATIC
		${VIDEO_SRC_LIST}
		${AR_ROOT_DIR}/lib/SRC/VideoAndroid/videoAndroid.c
		${AR_ROOT_DIR}/lib/SRC/VideoAndroid/sqlite3.c
		${AR_ROOT_DIR}/lib/SRC/VideoDummy/videoDummy.c
		${AR_ROOT_DIR}/lib/SRC/VideoImage/videoImage.c)

target_include_directories(arvideo PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android
                           ${AR_ROOT_DIR}/android/jni/curl/include)
