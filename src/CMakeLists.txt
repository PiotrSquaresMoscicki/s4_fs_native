set(S4_FS_NATIVE_INCLUDE ${CMAKE_CURRENT_LIST_DIR})

# gather source files list
file(GLOB_RECURSE S4_FS_NATIVE_SRCS RELATIVE ${CMAKE_CURRENT_LIST_DIR}
    ${S4_FS_NATIVE_INCLUDE}/*.cpp 
    ${S4_FS_NATIVE_INCLUDE}/*.hpp 
    ${S4_FS_NATIVE_INCLUDE}/*.hpp)
GenerateSourceGoups("${S4_FS_NATIVE_SRCS}")

add_library(${S4_FS_NATIVE_TARGET} STATIC ${S4_FS_NATIVE_SRCS})
target_compile_features(${S4_FS_NATIVE_TARGET} PUBLIC cxx_std_20)
target_include_directories(${S4_FS_NATIVE_TARGET} PUBLIC ${S4_FS_NATIVE_INCLUDE})

target_link_libraries(${S4_FS_NATIVE_TARGET} PUBLIC s4_fs)