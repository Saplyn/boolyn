# Basics

## Directory Structure

CMake is a build system generator. It generates build files in the specified
directory, usually `build/`, from the `CMakeLists.txt` file in the project
directory (top-level directory).

```plaintext
project_dir/
├── build/
│   ├── CMakeCache.txt
│   ├── CMakeFiles
│   │   └── ...
│   ├── cmake_install.cmake
│   └── Makefile
├── ...
└── CMakeLists.txt
```

## Build & Install Binary

```cmake
cmake_minimum_required(VERSION 3.22.1)
project(actual_project_name)

# Build executable
add_executable(executable_name main.cpp)

# Install binary to PATH
install(TARGETS executable_name DESTINATION bin)
```

## Build & Install Library

```cmake
cmake_minimum_required(VERSION 3.22.1)
project(actual_project_name)

# Build library
add_library(library_name lib.cpp)

# Install library to INCLUDE
install(TARGETS library_name DESTINATION lib)
```

## Linking Library

```cmake
# Linking system installed library
target_link_libraries(lab lab_lib)

# Linking library by path
target_link_directories(lab PRIVATE ${CMAKE_SOURCE_DIR}/build/)
```
