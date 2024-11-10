cmake_minimum_required(VERSION 3.5.0)
project(cubolt VERSION 0.1.0 LANGUAGES C CXX)

# Add GLAD source files
add_library(glad STATIC
    ${CMAKE_CURRENT_SOURCE_DIR}/deps/glad/glad.c
)

# Add include directories for GLAD
target_include_directories(glad PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/deps/glad
)

# Create executable
add_executable(cubolt src/main.cpp)

# Link libraries
target_link_libraries(cubolt 
    glfw
    glad
    ${CMAKE_DL_LIBS}  # Required on Linux
)

# Add include directories for the main executable
target_include_directories(cubolt PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/deps/glad
)