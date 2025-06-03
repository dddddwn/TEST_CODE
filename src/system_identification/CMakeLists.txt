add_library(SystemIdentification
    system_identification.cpp
    arx_rls.hpp
    system_identification.hpp
    signal_generator.hpp
    test_data.h
)

# 依赖 mathlib
target_include_directories(SystemIdentification PUBLIC
    ${CMAKE_SOURCE_DIR}/lib/mathlib
)

target_link_libraries(SystemIdentification
    mathlib
)

# 找到 GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

# arx_rls_test
add_executable(arx_rls_test arx_rls_test.cpp)
target_link_libraries(arx_rls_test SystemIdentification ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME arx_rls_test COMMAND arx_rls_test)

# system_identification_test
add_executable(system_identification_test system_identification_test.cpp)
target_link_libraries(system_identification_test SystemIdentification ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME system_identification_test COMMAND system_identification_test)
