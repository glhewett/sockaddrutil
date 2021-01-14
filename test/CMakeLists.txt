include ( CTest )

function (sa_test name)
  add_executable ( ${name}_test ${name}_test.c test_utils.c)
  target_link_libraries ( ${name}_test PRIVATE sockaddrutil)
  target_include_directories ( ${name}_test PRIVATE ../include )
  add_test ( NAME ${name} COMMAND ${name}_test )
endfunction()

sa_test ( sockaddr )

