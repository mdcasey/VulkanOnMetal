cmake_minimum_required(VERSION 3.0)

include_directories(../include)

include_directories(spirv_cross)
add_subdirectory(spirv_cross)

add_subdirectory(cube)
add_subdirectory(vulkaninfo)

add_definitions("-Wall -Wextra -Werror -Wno-unused-parameter -Wno-unused-value")
add_definitions("-DVK_USE_PLATFORM_MACOS_MVK")

include_directories(../include)

file(GLOB HEADERS *.h)
file(GLOB SOURCES *.mm)

add_library(VulkanOnMetal SHARED ${HEADERS} ${SOURCES})
set_property(TARGET VulkanOnMetal PROPERTY CXX_STANDARD 14)
target_link_libraries(VulkanOnMetal spirv_cross objc "-framework Metal")
