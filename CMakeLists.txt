cmake_minimum_required(VERSION 3.5)
project(sensors_description)

add_compile_options(-Wall -Wextra -Wpedantic -Wno-dev)

message(STATUS "Environment variable ROS_DISTRO = $ENV{ROS_DISTRO}")

# Check the ROS version and install the directories accordingly
if(DEFINED ENV{ROS_VERSION} AND $ENV{ROS_VERSION} EQUAL 2)

    # ROS2 colcon build
    find_package(ament_cmake REQUIRED)

    install(
        DIRECTORY xacro meshes
        DESTINATION share/${PROJECT_NAME}
    )

    ament_package()

elseif(DEFINED ENV{ROS_VERSION} AND $ENV{ROS_VERSION} EQUAL 1)

    # ROS1 catkin make
    find_package(catkin REQUIRED)

	catkin_package()

    install(
		DIRECTORY xacro
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/xacro
    )

	install(
		DIRECTORY meshes
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/meshes
    )

else()
	message(FATAL_ERROR "ROS_VERSION environment variable not set!")

endif()

