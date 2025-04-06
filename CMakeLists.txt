cmake_minimum_required(VERSION 3.20)
project(AllianceAndAllegiance VERSION 0.1.0 LANGUAGES C CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Platform-specific settings
if(WIN32)
    add_definitions(-DPLATFORM_WINDOWS)
elseif(UNIX AND NOT APPLE)
    add_definitions(-DPLATFORM_LINUX)
elseif(APPLE)
    add_definitions(-DPLATFORM_MACOS)
endif()

# Paths to external libraries
set(ENGINE_LIBS_DIR "K:/Alliance_and_Allengence/game_engine_libraries")
set(VULKAN_SDK_DIR "K:/VulkanSDK/1.4.304.1")
set(DXSDK_DIR "K:/Source/Microsoft DirectX SDK (June 2010)")


# Global include directories
# Include directories for libraries
include_directories(
    ${ENGINE_LIBS_DIR}/imgui-master/imgui-master
    ${ENGINE_LIBS_DIR}/glm-master
    ${ENGINE_LIBS_DIR}/bullet3-master/src
    ${ENGINE_LIBS_DIR}/assimp-master/assimp-master/include
    ${ENGINE_LIBS_DIR}/glfw-3.4.bin.WIN64/include
    ${ENGINE_LIBS_DIR}/openal-soft-master/include
    ${ENGINE_LIBS_DIR}/SocketLib
    ${ENGINE_LIBS_DIR}/stb-master/stb-master
    ${ENGINE_LIBS_DIR}/steamworks_sdk_161/public
    ${ENGINE_LIBS_DIR}/yojimbo-main/yojimbo-main/include
    ${VULKAN_SDK_DIR}/Include
    ${CMAKE_SOURCE_DIR}/public/directx/directx12
)
# Add subdirectories
add_subdirectory(launcher)
add_subdirectory(game/client)
add_subdirectory(game/server)
