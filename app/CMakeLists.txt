#指定需要CMAKE的最小版本
cmake_minimum_required(VERSION 3.4.1)


#C 的编译选项是 CMAKE_C_FLAGS
# 指定编译参数，可选
SET(CMAKE_CXX_FLAGS "-Wno-error=format-security -Wno-error=pointer-sign")

#设置生成的so动态库最后输出的路径
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../jniLibs/${ANDROID_ABI})

#设置头文件搜索路径（和此txt同个路径的头文件无需设置），可选
#INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/common)

#指定用到的系统库或者NDK库或者第三方库的搜索路径，可选。
#LINK_DIRECTORIES(/usr/local/lib)


add_library(
            # Sets the name of the library. 设置so库的名字，这里叫nativeBlurProcess
                nativeBlurProcess
            # Sets the library as a shared library.动态库，会被动态链接，在运行时被加载
                SHARED
            # Provides a relative path to your source file(s).要编译的源代码文件的路径，如果你的不是cpp下的，这里记得同步改下
                src/main/cpp/blur.c)

target_link_libraries( nativeBlurProcess
                        #加入该依赖库
                        jnigraphics
                        log )