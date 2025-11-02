cmake_minimum_required(VERSION 3.3)

set(PROJ_NAME glm_module)
project(${PROJ_NAME} CXX)

add_library(${PROJ_NAME} STATIC)

set_target_properties(${PROJ_NAME} PROPERTIES
  CXX_STANDARD 23
  POSITION_INDEPENDENT_CODE ON
)

target_compile_definitions(${PROJ_NAME} PRIVATE -DGLM_FORCE_DEPTH_ZERO_TO_ONE)
target_compile_definitions(${PROJ_NAME} PRIVATE -DGLM_ENABLE_EXPERIMENTAL)
target_compile_definitions(${PROJ_NAME} PRIVATE -DGLM_FORCE_CTOR_INIT)

target_include_directories(${PROJ_NAME} PRIVATE "third_party_libs/glm")
target_sources(${PROJ_NAME}
  PUBLIC
    FILE_SET cxx_modules TYPE CXX_MODULES FILES
    third_party_libs/glm/glm/glm.cppm
)
