# CMake file for building loudmouth for Windows
# =============================================
# /loudmouth/CMakeLists.txt


# Define the source files
# =======================
file(GLOB source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/*.c")
#file(GLOB header_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/*.h")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-connection.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-error.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-message-node.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-message.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-socket.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-ssl-generic.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/._lm-ssl-openssl.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/lm-asyncns-resolver.c")
#list(REMOVE_ITEM source_files_for_loudmouth "${CMAKE_SOURCE_DIR}/loudmouth/asyncns.c")
SET (loudmouthsrc 	
	             md5.c
	             lm-proxy.c  
	)


# Define include dirs
# ===================
set(LOUDMOUTH_INCLUDE_DIR ${CMAKE_SOURCE_DIR} ${CMAKE_SOURCE_DIR}/loudmouth)
include_directories(${LOUDMOUTH_INCLUDE_DIR} ${GLIB_INCLUDE_DIR} ${OPENSSL_INCLUDE_DIR})

# Define link dirs
# ================
link_directories(${OPENSLL_LINK_DIRECTORIES})

# Define the project
# ==================
add_library(loudmouth ${loudmouthsrc})
#set_target_properties(loudmouth PROPERTIES ${VERSION}) 
set_target_properties(loudmouth PROPERTIES PROJECT_LABEL "Loudmouth")
set_target_properties(loudmouth PROPERTIES LIBRARY_OUTPUT_DIRECTORY "bin")
target_link_libraries(loudmouth ${GLIB_LIBRARIES} ${OPENSLL_LIBRARIES})
add_definitions(-DLM_COMPILATION)