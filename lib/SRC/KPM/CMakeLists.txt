set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -Wall -fexceptions -frtti -Wno-extern-c-compat -Wno-null-conversion")

file(GLOB KPM_SRC_LIST *.c)
file(GLOB KPM_CPP_LIST *.cpp)

add_library(kpm STATIC
		${KPM_SRC_LIST}
		${KPM_CPP_LIST}
		FreakMatcher/detectors/DoG_scale_invariant_detector.cpp
		FreakMatcher/detectors/gaussian_scale_space_pyramid.cpp
		FreakMatcher/detectors/gradients.cpp
		FreakMatcher/detectors/harris.cpp
		FreakMatcher/detectors/orientation_assignment.cpp
		FreakMatcher/detectors/pyramid.cpp
		FreakMatcher/facade/visual_database_facade.cpp
		FreakMatcher/framework/date_time.cpp
		FreakMatcher/framework/image.cpp
		FreakMatcher/framework/logger.cpp
		FreakMatcher/framework/timers.cpp
		FreakMatcher/matchers/freak.cpp
		FreakMatcher/matchers/hough_similarity_voting.cpp)

target_include_directories(kpm PRIVATE
                           ${AR_ROOT_DIR}/include
                           ${AR_ROOT_DIR}/include/android
                           ${AR_ROOT_DIR}/lib/SRC/KPM/FreakMatcher)
