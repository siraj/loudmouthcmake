# CMake file for building loudmouth for Windows
# =============================================
# /CMakeLists.txt

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

set(CMAKE_SYSTEM_PREFIX_PATH ${CMAKE_SOURCE_DIR}/..) # the -config.cmake files are located here

# Define the solution
# ===================
project(loudmouth C) 
set (VERSION 1.4.3)


# Define external libraries
# =========================
FIND_PACKAGE(OpenSSL REQUIRED) 
FIND_PACKAGE(GLIBWIN32 REQUIRED)


# Define projects
# ================
add_subdirectory(loudmouth)
#add_subdirectory(examples)

