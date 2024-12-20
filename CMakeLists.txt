cmake_minimum_required(VERSION 3.22)

set(PROJECT_NAME pgm2dng)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

project(${PROJECT_NAME} VERSION 1.0 LANGUAGES CXX C)

#set(CMAKE_CXX_STANDARD 20)
#set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(SRC
    src/cxxopts.hpp
    src/dng_ext_image_writer.cpp
    src/dng_ext_image_writer.h
    src/pgm2dng.cpp
    src/targetver.h

    src/DNG/dng_1d_function.cpp
    src/DNG/dng_1d_function.h
    src/DNG/dng_1d_table.cpp
    src/DNG/dng_1d_table.h
    src/DNG/dng_abort_sniffer.cpp
    src/DNG/dng_abort_sniffer.h
    src/DNG/dng_area_task.cpp
    src/DNG/dng_area_task.h
    src/DNG/dng_assertions.h
    src/DNG/dng_auto_ptr.h
    src/DNG/dng_bad_pixels.cpp
    src/DNG/dng_bad_pixels.h
    #src/DNG/dng_big_table.cpp
    #src/DNG/dng_big_table.h
    src/DNG/dng_bottlenecks.cpp
    src/DNG/dng_bottlenecks.h
    src/DNG/dng_camera_profile.cpp
    src/DNG/dng_camera_profile.h
    src/DNG/dng_classes.h
    src/DNG/dng_color_space.cpp
    src/DNG/dng_color_space.h
    src/DNG/dng_color_spec.cpp
    src/DNG/dng_color_spec.h
    src/DNG/dng_date_time.cpp
    src/DNG/dng_date_time.h
    src/DNG/dng_errors.h
    src/DNG/dng_exceptions.cpp
    src/DNG/dng_exceptions.h
    src/DNG/dng_exif.cpp
    src/DNG/dng_exif.h
    src/DNG/dng_fast_module.h
    src/DNG/dng_file_stream.cpp
    src/DNG/dng_file_stream.h
    src/DNG/dng_filter_task.cpp
    src/DNG/dng_filter_task.h
    src/DNG/dng_fingerprint.cpp
    src/DNG/dng_fingerprint.h
    src/DNG/dng_flags.h
    src/DNG/dng_gain_map.cpp
    src/DNG/dng_gain_map.h
    src/DNG/dng_globals.cpp
    src/DNG/dng_globals.h
    src/DNG/dng_host.cpp
    src/DNG/dng_host.h
    src/DNG/dng_hue_sat_map.cpp
    src/DNG/dng_hue_sat_map.h
    src/DNG/dng_ifd.cpp
    src/DNG/dng_ifd.h
    src/DNG/dng_image.cpp
    src/DNG/dng_image.h
    src/DNG/dng_image_writer.cpp
    src/DNG/dng_image_writer.h
    src/DNG/dng_info.cpp
    src/DNG/dng_info.h
    src/DNG/dng_iptc.cpp
    src/DNG/dng_iptc.h
    src/DNG/dng_jpeg_image.cpp
    src/DNG/dng_jpeg_image.h
    src/DNG/dng_lens_correction.cpp
    src/DNG/dng_lens_correction.h
    src/DNG/dng_linearization_info.cpp
    src/DNG/dng_linearization_info.h
    src/DNG/dng_local_string.cpp
    src/DNG/dng_local_string.h
    src/DNG/dng_lossless_jpeg.cpp
    src/DNG/dng_lossless_jpeg.h
    src/DNG/dng_matrix.cpp
    src/DNG/dng_matrix.h
    src/DNG/dng_memory.cpp
    src/DNG/dng_memory.h
    src/DNG/dng_memory_stream.cpp
    src/DNG/dng_memory_stream.h
    src/DNG/dng_misc_opcodes.cpp
    src/DNG/dng_misc_opcodes.h
    src/DNG/dng_mosaic_info.cpp
    src/DNG/dng_mosaic_info.h
    src/DNG/dng_mutex.cpp
    src/DNG/dng_mutex.h
    src/DNG/dng_negative.cpp
    src/DNG/dng_negative.h
    src/DNG/dng_opcode_list.cpp
    src/DNG/dng_opcode_list.h
    src/DNG/dng_opcodes.cpp
    src/DNG/dng_opcodes.h
    src/DNG/dng_orientation.cpp
    src/DNG/dng_orientation.h
    src/DNG/dng_parse_utils.cpp
    src/DNG/dng_parse_utils.h
    src/DNG/dng_pixel_buffer.cpp
    src/DNG/dng_pixel_buffer.h
    src/DNG/dng_point.cpp
    src/DNG/dng_point.h
    src/DNG/dng_preview.cpp
    src/DNG/dng_preview.h
    src/DNG/dng_pthread.cpp
    src/DNG/dng_pthread.h
    src/DNG/dng_rational.cpp
    src/DNG/dng_rational.h
    src/DNG/dng_read_image.cpp
    src/DNG/dng_read_image.h
    src/DNG/dng_rect.cpp
    src/DNG/dng_rect.h
    src/DNG/dng_ref_counted_block.cpp
    src/DNG/dng_ref_counted_block.h
    src/DNG/dng_reference.cpp
    src/DNG/dng_reference.h
    src/DNG/dng_render.cpp
    src/DNG/dng_render.h
    src/DNG/dng_resample.cpp
    src/DNG/dng_resample.h
    #src/DNG/dng_safe_arithmetic.cpp
    #src/DNG/dng_safe_arithmetic.h
    src/DNG/dng_sdk_limits.h
    src/DNG/dng_shared.cpp
    src/DNG/dng_shared.h
    src/DNG/dng_simple_image.cpp
    src/DNG/dng_simple_image.h
    src/DNG/dng_spline.cpp
    src/DNG/dng_spline.h
    src/DNG/dng_stream.cpp
    src/DNG/dng_stream.h
    src/DNG/dng_string.cpp
    src/DNG/dng_string.h
    src/DNG/dng_string_list.cpp
    src/DNG/dng_string_list.h
    src/DNG/dng_tag_codes.h
    src/DNG/dng_tag_types.cpp
    src/DNG/dng_tag_types.h
    src/DNG/dng_tag_values.h
    src/DNG/dng_temperature.cpp
    src/DNG/dng_temperature.h
    src/DNG/dng_tile_iterator.cpp
    src/DNG/dng_tile_iterator.h
    src/DNG/dng_tone_curve.cpp
    src/DNG/dng_tone_curve.h
    src/DNG/dng_types.h
    src/DNG/dng_uncopyable.h
    src/DNG/dng_utils.cpp
    src/DNG/dng_utils.h
    #src/DNG/dng_validate.cpp
    src/DNG/dng_xmp.cpp
    src/DNG/dng_xmp.h
    src/DNG/dng_xmp_sdk.cpp
    src/DNG/dng_xmp_sdk.h
    src/DNG/dng_xy_coord.cpp
    src/DNG/dng_xy_coord.h
    src/DNG/RawEnvironment.h
)

add_executable(${PROJECT_NAME} ${SRC})

target_compile_definitions(${PROJECT_NAME} PRIVATE
    -DqDNGXMPDocOps=0
    -DqDNGValidateTarget=1
    -DqMacOS=0
    -DqWinOS=1
    -DqDNGUseLibJPEG=0
    -D_CRT_SECURE_NO_WARNINGS
)

target_include_directories(${PROJECT_NAME} PRIVATE
    src
    src/DNG
    #Libs/zlib
    Libs/libXMP/public/include
    Libs/LibTiff/include
)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(LIBS
        ${CMAKE_SOURCE_DIR}/Libs/libXMP/public/lib/x64/Debug/XMPCore.lib
        ${CMAKE_SOURCE_DIR}/Libs/libXMP/public/lib/x64/Debug/XMPFiles.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/debug/lib/jpeg.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/debug/lib/lzma.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/debug/lib/tiffd.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/debug/lib/turbojpeg.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/debug/lib/zlibd.lib
    )
else()
    set(LIBS
        ${CMAKE_SOURCE_DIR}/Libs/libXMP/public/lib/x64/Release/XMPCore.lib
        ${CMAKE_SOURCE_DIR}/Libs/libXMP/public/lib/x64/Release/XMPFiles.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/lib/jpeg.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/lib/lzma.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/lib/tiff.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/lib/turbojpeg.lib
        ${CMAKE_SOURCE_DIR}/Libs/LibTiff/lib/zlib.lib
    )
endif()

target_link_libraries(${PROJECT_NAME} PRIVATE
    ${LIBS}
)
