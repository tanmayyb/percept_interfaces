cmake_minimum_required(VERSION 3.18)
project(percept_interfaces)

# find dependencies
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

set(CMAKE_SKIP_BUILD_RPATH FALSE)
set(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# To generate messages and services
rosidl_generate_interfaces(${PROJECT_NAME}
    "srv/PosesToVectors.srv"
    "srv/AgentStateToCircForce.srv"
    "srv/AgentPoseToMinObstacleDist.srv"
  DEPENDENCIES geometry_msgs std_msgs # Add packages that above messages depend on, in this case geometry_msgs for Sphere.msg
)

ament_package()