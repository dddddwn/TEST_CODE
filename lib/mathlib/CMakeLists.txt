add_library(mathlib
    math/test/test.cpp
    math/filter/LowPassFilter2p.hpp
    math/filter/MedianFilter.hpp
    math/filter/NotchFilter.hpp
    math/filter/second_order_reference_model.hpp
    math/Functions.hpp
    math/Limits.hpp
    math/SearchMin.hpp
    math/TrajMath.hpp
    math/Utilities.hpp
    math/WelfordMean.hpp
    math/WelfordMeanVector.hpp
)

# 添加 GTest 支持并添加单元测试
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

add_executable(LowPassFilter2pVector3fTest math/test/LowPassFilter2pVector3fTest.cpp)
target_link_libraries(LowPassFilter2pVector3fTest mathlib ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME LowPassFilter2pVector3fTest COMMAND LowPassFilter2pVector3fTest)

add_executable(AlphaFilterTest math/test/AlphaFilterTest.cpp)
target_link_libraries(AlphaFilterTest mathlib ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME AlphaFilterTest COMMAND AlphaFilterTest)

add_executable(MedianFilterTest math/test/MedianFilterTest.cpp)
target_link_libraries(MedianFilterTest mathlib ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME MedianFilterTest COMMAND MedianFilterTest)

add_executable(NotchFilterTest math/test/NotchFilterTest.cpp)
target_link_libraries(NotchFilterTest mathlib ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME NotchFilterTest COMMAND NotchFilterTest)

add_executable(SecondOrderReferenceModelTest math/test/second_order_reference_model_test.cpp)
target_link_libraries(SecondOrderReferenceModelTest mathlib ${GTEST_BOTH_LIBRARIES} pthread)
add_test(NAME SecondOrderReferenceModelTest COMMAND SecondOrderReferenceModelTest)

# 你可以按需继续添加其他测试
