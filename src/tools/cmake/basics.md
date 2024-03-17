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

# Build Executable
add_executable(executable_name main.cpp)

# Install Binary to PATH
install(TARGETS executable_name DESTINATION bin)
```

## Build & Install Library

```cmake
cmake_minimum_required(VERSION 3.22.1)
project(actual_project_name)

# Build Library
add_library(library_name lib.cpp)

# Install Library to LIBRARY
install(TARGETS library_name DESTINATION lib)
```

## Linking Library

```cmake
# Linking Library
target_link_directories(lab PRIVATE ${CMAKE_SOURCE_DIR}/build/)
target_link_libraries(lab lab_lib)
```
