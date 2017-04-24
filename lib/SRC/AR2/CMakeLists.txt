set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti")

file(GLOB AR2_SRC_LIST *.c)

add_library(ar2 STATIC
		${AR2_SRC_LIST})

target_include_directories(ar2 PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android)
