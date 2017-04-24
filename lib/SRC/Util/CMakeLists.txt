set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti")

file(GLOB UTIL_SRC_LIST *.c)

add_library(util STATIC
		${UTIL_SRC_LIST})

target_include_directories(util PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android)
