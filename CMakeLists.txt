cmake_minimum_required(VERSION 3.5)
project(sensors_description)

find_package(catkin QUIET)
find_package(ament_cmake QUIET)

if(${catkin_FOUND})

    catkin_package()

    set(SHARE_DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

elseif(${ament_cmake_FOUND})

    ament_package()

    set(SHARE_DESTINATION share/${PROJECT_NAME})

endif()

# Install
install(
  DIRECTORY xacro
  DESTINATION ${SHARE_DESTINATION}
)

install(
  DIRECTORY meshes
  DESTINATION ${SHARE_DESTINATION}
)
