find_package(Boost CONFIG REQUIRED)

set(examples motivating_example0 get sample_printing quick_examples)

foreach(example ${examples})
  add_executable(${example} ${example}.cpp)
  target_link_libraries(${example} Boost::pfr Boost::headers)
  add_test(NAME ${example} COMMAND ${example})
endforeach()
