cmake_minimum_required(VERSION 3.0.2)
project(heron_gazebo)

find_package(catkin REQUIRED COMPONENTS
  xacro
)

catkin_package(CATKIN_DEPENDS xacro)

catkin_install_python(PROGRAMS
   scripts/activate_control_service
   scripts/cmd_drive_translate
   scripts/navsat_vel_translate
   scripts/rpy_translator
   scripts/twist_translate
   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# Generate world files from xacro and install
xacro_add_files(
  worlds/wildlife_task.world.xacro
  INSTALL DESTINATION worlds
)

install(DIRECTORY config launch worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
