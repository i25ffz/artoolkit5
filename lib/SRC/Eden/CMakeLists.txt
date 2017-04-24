set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti")

file(GLOB EDEN_SRC_LIST *.c)
file(GLOB EDEN_CPP_LIST *.cpp)
file(GLOB EDEN_GLUT_LIST gluttext/*.c)

add_library(eden STATIC
		${EDEN_SRC_LIST}
		${EDEN_GLUT_LIST}
		${EDEN_CPP_LIST})

target_include_directories(eden PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android)
