######### Default #########
cmake_minimum_required(VERSION 3.16)  
project(CPP_Mar19_2025 VERSION 0.0.1 LANGUAGES C CXX)

# Собираем все .cpp файлы в src/
file(GLOB_RECURSE SOURCES src/*.cpp)

# Создаём исполняемый файл
add_executable(${PROJECT_NAME} ${SOURCES})

# Включаем поддержку тестирования
include(CTest)
enable_testing()

# Настройки CPack (для генерации пакетов)
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

######### My Custom #########
#############################

# Устанавливаем стандарт C++
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Опционально: включаем предупреждения
if (CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic)
endif()
