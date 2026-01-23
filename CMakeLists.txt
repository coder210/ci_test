# CMakeLists.txt
cmake_minimum_required(VERSION 3.10)
project(MyCProject VERSION 1.0.0 LANGUAGES C)

# 设置 C 标准
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

# 编译选项
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -O0 -Wall -Wextra -Wpedantic -Werror")
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3 -march=native")
endif()

# 可执行文件
add_executable(myapp main.c)

# 安装配置
install(TARGETS myapp DESTINATION bin)
install(FILES main.c DESTINATION src)

# 测试支持
enable_testing()
add_test(NAME basic_test COMMAND myapp)

# 打包配置
set(CPACK_PACKAGE_NAME "${PROJECT_NAME}")
set(CPACK_PACKAGE_VERSION "${PROJECT_VERSION}")
set(CPACK_PACKAGE_DESCRIPTION "Simple C application")
set(CPACK_PACKAGE_CONTACT "developer@example.com")
set(CPACK_GENERATOR "TGZ;ZIP;DEB")
include(CPack)
