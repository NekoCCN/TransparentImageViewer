cmake_minimum_required (VERSION 3.8)

# 如果支持，请为 MSVC 编译器启用热重载。
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("TransparentImageViewer")

# SDL
add_subdirectory ("External/SDL")
include_directories ("External/SDL/include")

# SDL Extensions
add_subdirectory ("External/SDL_image")
include_directories ("External/SDL_image/include")
add_subdirectory ("External/SDL_ttf")
include_directories ("External/SDL_ttf/include")

# ImGui
add_subdirectory ("External/pre_imgui")
include_directories ("External/pre_imgui/imgui/include")

# 包含子项目。
add_subdirectory ("TransparentImageViewer")
