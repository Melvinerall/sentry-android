cmake_minimum_required(VERSION 3.10)
project(Sentry-Android LANGUAGES C CXX)

# Add sentry-android shared library
add_library(sentry-android SHARED src/main/jni/sentry.c)

# Adding sentry-native submodule subdirectory
add_subdirectory(${SENTRY_NATIVE_SRC} sentry_build)

# Link to sentry-native
target_link_libraries(sentry-android PRIVATE
    $<BUILD_INTERFACE:sentry::sentry>
)
