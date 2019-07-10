# create an executable
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${DEMO_APPLICATION_BINARY_DIR}/02-panda_force_control)
ADD_EXECUTABLE (controller02 controller.cpp)
ADD_EXECUTABLE (simviz02 simviz.cpp)

# and link the library against the executable
TARGET_LINK_LIBRARIES (controller02 ${DEMO_APPLICATION_COMMON_LIBRARIES})
TARGET_LINK_LIBRARIES (simviz02 ${DEMO_APPLICATION_COMMON_LIBRARIES})

# export resources such as model files.
# NOTE: this requires an install build
SET(APP_RESOURCE_DIR ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/resources)
FILE(MAKE_DIRECTORY ${APP_RESOURCE_DIR})
FILE(COPY world.urdf panda_arm.urdf DESTINATION ${APP_RESOURCE_DIR})