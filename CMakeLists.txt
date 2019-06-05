cmake_minimum_required(VERSION 3.10)

project(AudioFile)

add_library(AudioFile STATIC AudioFile.cpp)

target_compile_features(AudioFile PUBLIC cxx_std_11)

target_include_directories(AudioFile
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR})

target_compile_options(AudioFile
    PRIVATE
        $<$<OR:$<CXX_COMPILER_ID:Clang>,$<CXX_COMPILER_ID:AppleClang>,$<CXX_COMPILER_ID:GNU>>:
        -Wno-sign-compare>
		$<$<CXX_COMPILER_ID:MSVC>:
		/wd4389 /wd4244 /wd4245 /wd4458 /wd4457>
        )