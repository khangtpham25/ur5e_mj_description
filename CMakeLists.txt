cmake_minimum_required(VERSION 3.5)

project(ur5e_mj_description VERSION 1.0.0)

if(NOT TARGET mc_mujoco)
  find_package(mc_mujoco REQUIRED)
endif()

option(SRC_MODE "Use files in the repository instead of installed files" OFF)

set(UR5E_XML_MODEL_PATH "xml/ur5e.xml")
set(UR5E_PDGAINS_PATH "pdgains/PDgains_sim.dat")

if(SRC_MODE)
  set(UR5E_XML_MODEL_PATH "${CMAKE_CURRENT_SOURCE_DIR}/${UR5E_XML_MODEL_PATH}")
  set(UR5E_PDGAINS_PATH "${CMAKE_CURRENT_SOURCE_DIR}/${UR5E_PDGAINS_PATH}")
else()
  set(UR5E_XML_MODEL_PATH "${MC_MUJOCO_SHARE_DESTINATION}/UR5e/${UR5E_XML_MODEL_PATH}")
  set(UR5E_PDGAINS_PATH "${MC_MUJOCO_SHARE_DESTINATION}/UR5e/${UR5E_PDGAINS_PATH}")
endif()

configure_file(mc_mujoco/ur5e.in.yaml "${CMAKE_CURRENT_BINARY_DIR}/mc_mujoco/ur5e.yaml")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/mc_mujoco/ur5e.yaml" DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}")

install(DIRECTORY pdgains DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}/UR5e" FILES_MATCHING PATTERN "*.dat")
install(DIRECTORY xml DESTINATION "${MC_MUJOCO_SHARE_DESTINATION}/UR5e" FILES_MATCHING PATTERN "*.xml" PATTERN "*.obj")
