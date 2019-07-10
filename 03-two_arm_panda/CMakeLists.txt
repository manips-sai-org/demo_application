# create an executable
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${DEMO_APPLICATION_BINARY_DIR}/03-two_arm_panda)
ADD_EXECUTABLE (controller03 controller.cpp)
ADD_EXECUTABLE (simviz03 simviz.cpp)
ADD_EXECUTABLE (simviz03_grippers simviz_grippers.cpp)

# and link the library against the executable
TARGET_LINK_LIBRARIES (controller03 ${DEMO_APPLICATION_COMMON_LIBRARIES})
TARGET_LINK_LIBRARIES (simviz03 ${DEMO_APPLICATION_COMMON_LIBRARIES})
TARGET_LINK_LIBRARIES (simviz03_grippers ${DEMO_APPLICATION_COMMON_LIBRARIES})

# export resources such as model files.
# NOTE: this requires an install build
SET(APP_RESOURCE_DIR ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/resources)
FILE(MAKE_DIRECTORY ${APP_RESOURCE_DIR})
FILE(COPY world.urdf world_grippers.urdf DESTINATION ${APP_RESOURCE_DIR})
FILE(COPY panda_arm.urdf DESTINATION ${APP_RESOURCE_DIR})
FILE(COPY panda_arm_hand.urdf DESTINATION ${APP_RESOURCE_DIR})