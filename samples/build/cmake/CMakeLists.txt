# =================================================================================================
# ADOBE SYSTEMS INCORPORATED
# Copyright 2013 Adobe Systems Incorporated
# All Rights Reserved
#
# NOTICE: Adobe permits you to use, modify, and distribute this file in accordance with the terms
# of the Adobe license agreement accompanying it.
# =================================================================================================

# define minimum cmake version
cmake_minimum_required(VERSION 2.8.6)

SET(CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "Configurations" FORCE)
#This projects relative path to XMP Root
set ( XMP_THIS_PROJECT_RELATIVEPATH "../../../")

# Set the project name according to target
if(CMAKE_CL_64)
	set(IS64BIT "TRUE")
	set (POSTFIX "_x64")
	project(XMP_Samples_64)
	message (INFO ":64 Target is chosen")
else(CMAKE_CL_64)
	set(IS64BIT "FALSE")
	project(XMP_Samples)
	message (INFO ":32 bit target is chosen")
endif(CMAKE_CL_64)

set(TESTXMP_VERSION 1.0)

#setting static flag for correct compiler flag through shared config
set (XMP_BUILD_STATIC 1)
# ==============================================================================
# load shared config
# ==============================================================================
include(SharedConfig.cmake)

# common path defines
# setup project specific paths
set( PROJECT_ROOT ${PROJECT_SOURCE_DIR})
set( SAMPLE_SOURCE_ROOT ${PROJECT_ROOT}/../../source/)
set( XMP_SDK_ROOT ${PROJECT_ROOT}/../../.. )
set( PUBLIC_INCLUDE ${XMP_SDK_ROOT}/public/include)

# Output of test executables
set(OUTPUT_DIR ${SAMPLE_SOURCE_ROOT}/target/${PLATFORM_FOLDER}/)

# Add the Samples to the project
	message (INFO ":Add CustomSchema sample")
	add_subdirectory(${PROJECT_ROOT}/CustomSchema ${PROJECT_ROOT}/CustomSchema/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/DumpFile ${PROJECT_ROOT}/DumpFile/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/DumpMainXMP ${PROJECT_ROOT}/DumpMainXMP/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/DumpScannedXMP ${PROJECT_ROOT}/DumpScannedXMP/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/ModifyingXMP ${PROJECT_ROOT}/ModifyingXMP/build${POSTFIX})	
	add_subdirectory(${PROJECT_ROOT}/ReadingXMP ${PROJECT_ROOT}/ReadingXMP/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/XMPCommand ${PROJECT_ROOT}/XMPCommand/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/XMPCoreCoverage ${PROJECT_ROOT}/XMPCoreCoverage/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/XMPFilesCoverage ${PROJECT_ROOT}/XMPFilesCoverage/build${POSTFIX})
	add_subdirectory(${PROJECT_ROOT}/XMPIterations ${PROJECT_ROOT}/XMPIterations/build${POSTFIX})

message (STATUS "===========================================================================")
message (STATUS " ${PROJECT_NAME} ")
message (STATUS "===========================================================================")


