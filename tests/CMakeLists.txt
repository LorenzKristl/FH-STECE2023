add_executable(
  door-tests

  door-tests.cpp
  timespec-tests.cpp
)
target_link_libraries(
  door-tests

  door
  gtest_main 
)
add_test(
  NAME door-tests 
  COMMAND door-tests
)

if (LIBGPIOD_FOUND)
  add_executable(gpio-read-value-loop gpio-read-value-loop.cpp)
  target_link_libraries(gpio-read-value-loop LIBGPIOD::LIBGPIOD)
else()
  message(WARNING "Not building gpio-read-value-loop because libgpiod not found")
endif()

add_executable(
  motorLED-tests

  motorLED-tests.cpp
)

target_link_libraries(
  motorLED-tests

  door
)

  target_link_libraries(motorLED-tests LIBGPIOD::LIBGPIOD)