# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

add_definitions(-DCPPHTTPLIB_OPENSSL_SUPPORT)

set(inc_DIR openssl/${ANDROID_ABI}/include/)
set(libs_DIR openssl/${ANDROID_ABI}/lib/)

include_directories(${inc_DIR})
LINK_DIRECTORIES(${libs_DIR})

add_library(local_crypto STATIC IMPORTED)
set_target_properties(local_crypto PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/openssl/${ANDROID_ABI}/lib/libcrypto.a)

add_library(local_ssl STATIC IMPORTED)
set_target_properties(local_ssl PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/openssl/${ANDROID_ABI}/lib/libssl.a)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
        cipher

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        src/main/cpp/cipher.cpp
        src/main/cpp/zsd.cpp)

find_library(log-lib log)
find_library(z-lib z)

target_link_libraries( # Specifies the target library.
        cipher
        # Links the target library to the log library
        # included in the NDK.
        local_ssl
        local_crypto
        ${z-lib}
        ${log-lib})
