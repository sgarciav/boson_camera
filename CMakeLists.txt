cmake_minimum_required(VERSION 2.8.3)

project(boson_camera)

find_package(catkin_simple REQUIRED)

catkin_simple(ALL_DEPS_REQUIRED)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O3")

find_package(OpenCV REQUIRED)

set(SRC_FOLDER src)

cs_add_executable(
        ${PROJECT_NAME}
        ${SRC_FOLDER}/boson_ros_node.cpp
        ${SRC_FOLDER}/boson_camera.cpp
)
target_link_libraries(${PROJECT_NAME}
        ${catkin_LIBRARIES}
        ${OpenCV_LIBRARIES}
        )

cs_install()

## Mark other files for installation (e.g. launch and bag files, etc.)
install(DIRECTORY config
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  )

cs_export()
