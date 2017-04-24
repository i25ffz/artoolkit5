set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti -DHAVE_ARM_NEON=1")

file(GLOB AR_SRC_LIST *.c)
file(GLOB ARSUB_SRC_LIST arLabelingSub/*.c)

add_library(ar STATIC
		${AR_SRC_LIST}
		${ARSUB_SRC_LIST})

target_include_directories(ar PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android)
