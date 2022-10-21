cmake_minimum_required(VERSION 3.0.0)

project(FFMPEG VERSION 1.0.0)


find_path(AVCODEC_INCLUDE_DIR avcodec.h ##standard template NAME_INCLUDE_DIR
PATHS /usr/local/ffmpeg/include/libavcodec
)
find_library(AVCODEC_LIBRARY avcodec  ##standard template NAME_LIBRARY
PATHS /usr/local/ffmpeg/lib
)


find_path(AVFORMAT_INCLUDE_DIR avformat.h
PATHS /usr/local/ffmpeg/include/libavformat
)
find_library(AVFORMAT_LIBRARY avformat  ##standard template NAME_LIBRARY
PATHS /usr/local/ffmpeg/lib
)

find_path(AVUTIL_INCLUDE_DIR avutil.h
PATHS /usr/local/ffmpeg/include/libavutil)
find_library(AVUTIL_LIBRARY avutil
PATHS /usr/local/ffmpeg/lib
)

find_path(AVDEVICE_INCLUDE_DIR avdevice.h
PATHS /usr/local/ffmpeg/include/libavdevice
)
find_library(AVDEVICE_LIBRARY avdevice
PATHS /usr/local/ffmpeg/lib
)


find_path(SWSCALE_INCLUDE_DIR swscale.h
PATHS /usr/local/ffmpeg/include/libswscale
)
find_library(SWSCALE_LIBRARY swscale
PATHS /usr/local/ffmpeg/lib
)


find_path(SWRESAMPLE_INCLUDE_DIR swresample.h
PATHS /usr/local/ffmpeg/include/libswresample
)
find_library(SWRESAMPLE_LIBRARY swresample
PATHS /usr/local/ffmpeg/lib
)


add_executable(FFMPEG
main.cpp 
)

#[[target_include_directories(FFMPEG PRIVATE ${AVCODEC_INCLUDE_DIR} ${AVFORMAT_INCLUDE_DIR} ${AVUTIL_INCLUDE_DIR} ${AVDEVICE_INCLUDE_DIR})
target_link_libraries(FFMPEG PRIVATE ${AVCODEC_LIBRARY} ${AVFORMAT_LIBRARY} ${AVUTIL_LIBRARY} ${AVDEVICE_LIBRARY})]]

target_include_directories(FFMPEG PRIVATE ${AVCODEC_INCLUDE_DIR} ${AVFORMAT_INCLUDE_DIR} ${AVUTIL_INCLUDE_DIR} ${AVDEVICE_INCLUDE_DIR} ${SWSCALE_INCLUDE_DIR} ${SWRESAMPLE_INCLUDE_DIR})
target_link_libraries(FFMPEG PRIVATE ${AVCODEC_LIBRARY} ${AVFORMAT_LIBRARY} ${AVUTIL_LIBRARY} ${AVDEVICE_LIBRARY} ${SWSCALE_LIBRARY} ${SWRESAMPLE_LIBRARY})


#[[target_include_directories(FFMPEG PRIVATE /usr/local/ffmpeg/include)
target_link_libraries(FFMPEG PRIVATE /usr/local/ffmpeg/lib/libavcodec.so)]]


