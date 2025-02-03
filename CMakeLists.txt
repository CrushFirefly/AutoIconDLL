cmake_minimum_required(VERSION 3.20)
project(AutoIconDLL)

# 1. 定义图标文件夹路径
set(ICON_DIR "${CMAKE_CURRENT_SOURCE_DIR}/resources")

# 2. 遍历所有 .ico 文件
file(GLOB_RECURSE ICON_FILES "${ICON_DIR}/*.ico")

# 3. 生成资源脚本内容
set(RC_CONTENT "")
foreach(ICON_FILE ${ICON_FILES})
    # 提取文件名（不带扩展名）作为资源标识符
    get_filename_component(ICON_NAME ${ICON_FILE} NAME_WE)
    # 生成资源行，例如：IDI_ICON_1 ICON "resources/icon1.ico"
    string(APPEND RC_CONTENT "IDI_ICON_${ICON_NAME} ICON \"${ICON_FILE}\"\n")
endforeach()

# 4. 写入生成的 .rc 文件
set(GENERATED_RC "${CMAKE_CURRENT_BINARY_DIR}/generated/auto_resources.rc")
file(WRITE ${GENERATED_RC} ${RC_CONTENT})

# 5. 生成 DLL 并包含资源文件
add_library(AutoIconDLL SHARED
        src/main.cpp
        ${GENERATED_RC}  # 包含自动生成的资源文件
)

# 6. 确保资源编译器配置（Windows）
if(WIN32)
    set(CMAKE_RC_COMPILER_INIT windres)
    enable_language(RC)
    set(CMAKE_RC_COMPILE_OBJECT "<CMAKE_RC_COMPILER> -O coff <DEFINES> <INCLUDES> <FLAGS> <SOURCE> <OBJECT>")
endif()