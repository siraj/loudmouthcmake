# CMake file for building loudmouth for Windows
# =============================================
# /loudmouth/CMakeLists.txt


FIND_PROGRAM(MKENUM glib-genmarshal ${GLIB_RUNTIME}) 
EXECUTE_PROCESS(COMMAND ${MKENUM} "--header" "--prefix=_lm_marshal" 
	INPUT_FILE ${CMAKE_SOURCE_DIR}/loudmouth/lm-marshal.list
	OUTPUT_FILE ${CMAKE_SOURCE_DIR}/loudmouth/lm-marshal.h
	)

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
		 lm-socket.c
		 lm-sock.c
		 lm-parser.c
		 lm-sasl.c
		 lm-message.c
		 lm-debug.c 
		 lm-connection.c
		 lm-ssl-openssl.c 
		 base64.c
		 lm-error.c
		 lm-message-handler.c
		 lm-message-node.c
		 lm-message-queue.c
		 lm-message.c
		 lm-sha.c
		 lm-ssl-base.c
		 lm-ssl-generic.c
		 lm-utils.c
		 lm-misc.c
		 lm-ssl-gnutls.c
		 )


# Define include dirs
# ===================
set(LOUDMOUTH_INCLUDE_DIR ${CMAKE_SOURCE_DIR} ${CMAKE_SOURCE_DIR}/loudmouth)
include_directories(${LOUDMOUTH_INCLUDE_DIR} 
	            ${GLIBWIN32_INCLUDE_DIR} 
		    ${OPENSSL_INCLUDE_DIR}
		    ${EXTRA_INCLUDE_DIR})

# Define link dirs
# ================
link_directories(${OPENSLL_LINK_DIRECTORIES})

# Define the project
# ==================
add_library(loudmouth SHARED ${loudmouthsrc})
#set_target_properties(loudmouth PROPERTIES ${VERSION}) 
set_target_properties(loudmouth PROPERTIES PROJECT_LABEL "Loudmouth")
set_target_properties(loudmouth PROPERTIES LIBRARY_OUTPUT_DIRECTORY "bin")
target_link_libraries(loudmouth ${GLIBWIN32_LIBRARIES} ${OPENSLL_LIBRARIES})
add_definitions(-DLM_COMPILATION)
