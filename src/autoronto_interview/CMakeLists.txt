

cmake_minimum_required(VERSION 3.8)
project(autoronto_interview)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(test_publisher src/test_publisher.cpp)
ament_target_dependencies(test_publisher rclcpp std_msgs)

install(TARGETS
   test_publisher
   DESTINATION lib/${PROJECT_NAME}
 )

 add_executable(solution src/solution.cpp)
 ament_target_dependencies(solution rclcpp std_msgs)

install(TARGETS
  test_publisher
  solution
  DESTINATION lib/${PROJECT_NAME})

ament_package()

