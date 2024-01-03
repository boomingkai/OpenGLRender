cmake_minimum_required(VERSION 3.10)
project (OpenGLRender)

set(SOURCES
    src/main.c
)

add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries( ${PROJECT_NAME}
    PRIVATE
        OpenGL32.lib
		glew32s.lib
		glfw3.lib
		../lib/Debug/GLUS
		kernel32.lib
		user32.lib
		gdi32.lib
		winspool.lib
		shell32.lib
		ole32.lib
		oleaut32.lib
		uuid.lib
		comdlg32.lib
		advapi32.lib
)

target_include_directories(${PROJECT_NAME}
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/GLFW/include
		${PROJECT_SOURCE_DIR}/GLUS/src
		${PROJECT_SOURCE_DIR}/External/x86/Windows/MSVC/include
)#设置这个可执行文件OpenGLRender需要包含的库的路径


# 设置资源文件夹的路径
set(THIRD_DIR ${PROJECT_SOURCE_DIR}/Third-Party)

# 设置生成的编译文件夹的路径
set(BUILD_DIR ${PROJECT_SOURCE_DIR}/build)


# 获取资源文件夹中的所有文件列表
file(GLOB RESOURCE_FILES "${THIRD_DIR}/*")

# 将资源文件夹中的文件复制到生成的编译文件夹中
file(COPY ${RESOURCE_FILES} DESTINATION ${BUILD_DIR})

add_subdirectory(GLUS)

set_property(DIRECTORY ${PROJECT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${PROJECT_NAME})

