cmake_minimum_required(VERSION 3.10)
project(MyCProject C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_executable(myapp main.c)

# 如果有头文件，可以包含进来，例如：
# target_include_directories(myapp PRIVATE include)

# 设置编译选项，例如：
# target_compile_options(myapp PRIVATE -Wall -Wextra -Werror)

# 安装目标（可选）
# install(TARGETS myapp DESTINATION bin)
