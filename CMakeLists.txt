# It's recommended to set a minimum CMake version.
# If you use CMake features from higher versions, update this to match.
cmake_minimum_required(VERSION 3.24)

# Set your project name. This will be the name of your SKSE .dll file.
project(HelloWorld VERSION 0.0.1 LANGUAGES CXX)

# Set <DEPLOY_ROOT> to set the path of a mod to deploy files to.
# Defaults to the value of environment variable SKYRIM_MODS_FOLDER
set(DEPLOY_ROOT "$ENV{SKYRIM_MODS_FOLDER}")
# The SKSE plugin files will be writen to <DEPLOY_ROOT>/<PROJECT_NAME>/SKSE/Plugins
# set(DEPLOY_ROOT "C:/some/path/to/mod/path") # <--- uncomment line to customize

# Setup your SKSE plugin as an SKSE plugin!
find_package(CommonLibSSE CONFIG REQUIRED)
add_commonlibsse_plugin(${PROJECT_NAME} SOURCES plugin.cpp) # <--- specifies plugin.cpp
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_23) # <--- use C++23 standard
target_precompile_headers(${PROJECT_NAME} PRIVATE PCH.h) # <--- PCH.h is required!

# When your SKSE .dll is compiled, this will automatically copy the .dll into your mods folder.
# Only works if you configure DEPLOY_ROOT above (or set the SKYRIM_MODS_FOLDER environment variable)
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
