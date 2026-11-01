cmake_minimum_required(VERSION 3.16)
project(ros_ethercat_eml)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

find_package(ament_cmake REQUIRED)

# Only the POSIX raw-socket driver is built (as in the ROS1 package); the Xenomai
# header ethercat_xenomai_drv.h is declaration-only and needs no Xenomai headers.
set(CMAKE_POSITION_INDEPENDENT_CODE ON)
add_library(${PROJECT_NAME}
  src/ethercat_AL.cxx
  src/ethercat_FSM.cxx
  src/ethercat_master.cxx
  src/ethercat_mbx.cxx
  src/ethercat_process_data.cxx
  src/ethercat_router.cxx
  src/ethercat_slave_conf.cxx
  src/ethercat_slave_handler.cxx
  src/ethercat_device_addressed_telegram.cxx
  src/ethercat_dll.cxx
  src/ethercat_frame.cxx
  src/ethercat_logical_addressed_telegram.cxx
  src/ethercat_slave_memory.cxx
  src/ethercat_telegram.cxx
  src/ethercat_posix_drv.cxx
)
target_include_directories(${PROJECT_NAME} PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include/${PROJECT_NAME}>
)

install(DIRECTORY include/ DESTINATION include/${PROJECT_NAME})
install(TARGETS ${PROJECT_NAME} EXPORT export_${PROJECT_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

ament_export_targets(export_${PROJECT_NAME} HAS_LIBRARY_TARGET)
ament_package()
