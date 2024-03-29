set(S4_FS_NATIVE_TEST_INCLUDE ${CMAKE_CURRENT_LIST_DIR})

# gather source files list
file(GLOB_RECURSE S4_FS_NATIVE_TEST_SRCS RELATIVE ${CMAKE_CURRENT_LIST_DIR}
    ${S4_FS_NATIVE_TEST_INCLUDE}/*.cpp 
    ${S4_FS_NATIVE_TEST_INCLUDE}/*.hpp 
    ${S4_FS_NATIVE_TEST_INCLUDE}/*.hpp)
GenerateSourceGoups("${S4_FS_NATIVE_TEST_SRCS}")

add_executable(${S4_FS_NATIVE_TEST_TARGET} ${S4_FS_NATIVE_TEST_SRCS})
target_compile_features(${S4_FS_NATIVE_TEST_TARGET} PUBLIC cxx_std_20)
target_include_directories(${S4_FS_NATIVE_TEST_TARGET} PUBLIC ${S4_FS_NATIVE_TEST_INCLUDE})

target_link_libraries(${S4_FS_NATIVE_TEST_TARGET} PRIVATE ${S4_FS_NATIVE_TARGET} Catch2::Catch2WithMain)

include(CTest)
include(Catch)
catch_discover_tests(${S4_FS_NATIVE_TEST_TARGET} REPORTER console)