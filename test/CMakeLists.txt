find_package(Boost CONFIG REQUIRED)

set(tests loophole_detection offset_based_getter print_config)

foreach(test ${tests})
  add_executable(${test} ${test}.cpp)
  target_link_libraries(${test} Boost::pfr Boost::headers)
  add_test(NAME ${test} COMMAND ${test})
endforeach()

set(test test_tuple_sizes_on)
foreach(type uint8_t int16_t int32_t uint64_t)
  set(name ${test}_${type})
  add_executable(${name} ${test}.cpp)
  target_link_libraries(${name} Boost::pfr Boost::headers)
  target_compile_definitions(${name} PRIVATE BOOST_PFR_RUN_TEST_ON=${type})
  add_test(NAME ${name} COMMAND ${name})
endforeach()
