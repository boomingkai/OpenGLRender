cmake_minimum_required(VERSION 3.10)
project (OpenGLRender)

set(SOURCES
    src/main.c
)

add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries( ${PROJECT_NAME}
    PRIVATE
        gdi32.lib
		winspool.lib
		shell32.lib
		ole32.lib
		oleaut32.lib
		uuid.lib
		comdlg32.lib
		advapi32.lib
)

target_include_directories(hello_headers
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/GLFW/include
		${PROJECT_SOURCE_DIR}/GLUS/src
		${PROJECT_SOURCE_DIR}/External/x86/Windows/MSVC/include
)#设置这个可执行文件OpenGLRender需要包含的库的路径