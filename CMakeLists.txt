cmake_minimum_required(VERSION 3.21)

project(HelloWorld VERSION 0.0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(DEPLOY_MOD "Copy mod .dll and resource into %SKYRIM_MODS_DEPLOY_ROOT%\\${PROJECT_NAME}" OFF)

# Override <DEPLOY_ROOT> to set the path of a mod to deploy files to.
# The SKSE plugin files will be writen to <DEPLOY_ROOT>/<PROJECT_NAME>/SKSE/Plugins
# You can use the environment variable SKYRIM_MODS_DEPLOY_ROOT to set a default <DEPLOY_ROOT>
# set(DEPLOY_ROOT "C:/some/path/to/mod/path")

set(SOURCE_FILES plugin.cpp)

find_package(CommonLibSSE CONFIG REQUIRED)
add_commonlibsse_plugin(${PROJECT_NAME} SOURCES ${SOURCE_FILES})
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_23)
target_precompile_headers(${PROJECT_NAME} PUBLIC PCH.h)

if(DEPLOY_MOD)
	if(EXISTS "${DEPLOY_ROOT}")
        set(MOD_FOLDER "${DEPLOY_ROOT}/${PROJECT_NAME}")
        set(DLL_FOLDER "${MOD_FOLDER}/SKSE/Plugins")
        message(STATUS "Plugin output directory: ${MOD_FOLDER}")
        add_custom_command(
            TARGET "${PROJECT_NAME}"
            POST_BUILD
            COMMAND "${CMAKE_COMMAND}" -E make_directory    "${DLL_FOLDER}"
            COMMAND "${CMAKE_COMMAND}" -E copy_if_different "$<TARGET_FILE:${PROJECT_NAME}>"     "${DLL_FOLDER}/$<TARGET_FILE_NAME:${PROJECT_NAME}>"
            COMMAND "${CMAKE_COMMAND}" -E copy_if_different "$<TARGET_PDB_FILE:${PROJECT_NAME}>" "${DLL_FOLDER}/$<TARGET_PDB_FILE_NAME:${PROJECT_NAME}>"
            VERBATIM
        )
    endif()
endif()
