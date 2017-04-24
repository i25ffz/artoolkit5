set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti -DHAVE_ARM_NEON=1")

add_library(argsub_es STATIC
		gsub_es.c
		glStateCache.c
		gsub_mtx.c)

target_include_directories(argsub_es PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android)
