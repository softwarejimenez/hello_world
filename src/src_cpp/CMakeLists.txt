STRING(TOLOWER "${CMAKE_BUILD_TYPE}" CMAKE_BUILD_TYPE_LOWER)

if(CMAKE_BUILD_TYPE_LOWER STREQUAL "debug")
    message(STATUS "Debug mode")
    add_executable(hello_world_cppd "${CMAKE_CURRENT_SOURCE_DIR}/src/hello_world_cpp.cpp")
    target_include_directories(
        hello_world_cppd
        PRIVATE
            "${CMAKE_CURRENT_SOURCE_DIR}/include"
    )
    SET(CODE_COVERAGE OFF CACHE BOOLEAN "User-specified option to enable coverage reporting")
    if(CODE_COVERAGE)
        message(STATUS "Code Coverage mode")
        target_compile_options(hello_world_cppd PRIVATE
            -O0        # no optimization
            -g         # generate debug info
            --coverage # sets all required flags
        )
        if(CMAKE_VERSION VERSION_GREATER_EQUAL 3.13)
        target_link_options(hello_world_cppd PRIVATE --coverage)
      else()
        target_link_libraries(hello_world_cppd PRIVATE --coverage)
      endif()
    endif()
endif()


if(CMAKE_BUILD_TYPE_LOWER STREQUAL "release")
    message(STATUS "Release mode")
    add_executable(hello_world_cpp "${CMAKE_CURRENT_SOURCE_DIR}/src/hello_world_cpp.cpp")
    target_include_directories(
        hello_world_cpp
        PRIVATE
            "${CMAKE_CURRENT_SOURCE_DIR}/include"
    )
ENDIF()
message(STATUS "Compiled hello_world_cpp")

if(BUILD_TESTING)
    enable_testing()
    add_executable(test_cpp "${CMAKE_CURRENT_SOURCE_DIR}/test/test.cpp")
    target_include_directories(
        test_cpp
        PRIVATE
            "${CMAKE_CURRENT_SOURCE_DIR}/include"
    )
    add_test(
        NAME test
        COMMAND test_cpp)
endif()
