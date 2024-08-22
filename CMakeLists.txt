cmake_minimum_required(VERSION 3.23)
project(LearnVulkan)

file(GLOB src_files
     "src/*.cpp"
)

add_executable(${PROJECT_NAME} ${src_files})

find_package(Vulkan REQUIRED)

include(FetchContent)
FetchContent_Declare(
    glfw
    GIT_REPOSITORY https://github.com/glfw/glfw.git
)
FetchContent_MakeAvailable(glfw)

target_include_directories(${PROJECT_NAME}
    PUBLIC  ${Vulkan_INCLUDE_DIRS}
    PUBLIC  include/lve_window
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE glfw
    PRIVATE Vulkan::Vulkan
)

