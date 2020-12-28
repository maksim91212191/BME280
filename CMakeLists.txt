cmake_minimum_required(VERSION 3.0)
project(bme)

set(LIB_TARGET ${PROJECT_NAME}${PLATFORM_EXEC_SUFFIX})

set(SOURCES
  ./Source/bme280.cpp
  )

set(HEADERS
  ./Include/bme/bme280.h
  ./Include/bme/BME280CalibrationData.h
  ./Include/bme/BME280Data.h
  ./Include/bme/BME280RawData.h
  )

add_definitions(-lwiringPi)

add_library(${LIB_TARGET} ${SOURCES} ${HEADERS})

target_include_directories(${LIB_TARGET}
  PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/Include
  PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/Include/bme)

target_compile_definitions(${LIB_TARGET} PUBLIC TMS320C66X)
