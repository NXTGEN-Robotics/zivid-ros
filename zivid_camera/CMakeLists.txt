cmake_minimum_required(VERSION 3.5)
project(zivid_camera LANGUAGES CXX)

if(${CMAKE_VERSION} VERSION_LESS "3.8.0")
  add_compile_options(-std=c++17)
else()
  set(CMAKE_CXX_STANDARD 17)
endif()

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
  std_msgs
  message_generation
)


add_service_files(
  DIRECTORY
  srv
  FILES
  Capture.srv
  Capture2D.srv
  CaptureAssistantSuggestSettings.srv
  LoadSettingsFromFile.srv
  LoadSettings2DFromFile.srv
  CameraInfoModelName.srv
  CameraInfoSerialNumber.srv
  IsConnected.srv
)
generate_messages(
  DEPENDENCIES
  sensor_msgs
)
catkin_package(
  INCLUDE_DIRS ${catkin_INCLUDE_DIRS}
  # LIBRARIES ${LIBRARY_NAME}
  CATKIN_DEPENDS message_runtime sensor_msgs std_msgs
)