set(TESTING_GTEST_DIR ${CMAKE_CURRENT_SOURCE_DIR}/googletest)
set(TESTING_GBENCHMARK_DIR ${CMAKE_CURRENT_SOURCE_DIR}/googlebenchmark)

if(NOT EXISTS ${TESTING_GTEST_DIR})
    message(FATAL_ERROR "[COMPONENTS] Error searching for GTest: directory ${TESTING_GTEST_DIR} not exist")
endif()

if(NOT EXISTS ${TESTING_GBENCHMARK_DIR})
    message(FATAL_ERROR "[COMPONENTS] Error searching for GBenchmark: directory ${TESTING_GBENCHMARK_DIR} not exist")
endif()

enable_testing()
add_subdirectory(${TESTING_GTEST_DIR})  # Linking: GTest::gtest, GTest::gtest_main

set( BENCHMARK_ENABLE_GTEST_TESTS OFF CACHE BOOL "Unused feature" FORCE)
set( BENCHMARK_ENABLE_INSTALL     OFF CACHE BOOL "Unused feature" FORCE)
set( BENCHMARK_ENABLE_TESTING     OFF CACHE BOOL "Unused feature" FORCE)
set( BENCHMARK_ENABLE_WERROR      OFF CACHE BOOL "Unused feature" FORCE)
set( BENCHMARK_INSTALL_DOCS       OFF CACHE BOOL "Unused feature" FORCE)
set( BENCHMARK_INSTALL_TOOLS      OFF CACHE BOOL "Unused feature" FORCE)
add_subdirectory(${TESTING_GBENCHMARK_DIR})
