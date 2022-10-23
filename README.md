# ALGLIB
The mathematical *ALGLIB* library for C++ with CMake support.

## Usage

The integration of *ALGLIB* into a code base using this repository can be done like this:


```bash
  cd project-root
  git submodule add https://github.com/erl987/alglib.git libraries/Alglib
```


Now add this subdirectory in the `CMakeLists.txt` file in the project root directory:

```CMake
  add_subdirectory(libraries/Alglib)
```

Link it in the `CMakeLists.txt` file where ALGLIB is used:

```CMake
  target_link_libraries(project PUBLIC Alglib) 
```

Optionally compiler optimizations can be enabled

```CMake
  # enable SSE-optimizations for the Alglib-library on the supported platforms
  if (${CMAKE_SYSTEM_PROCESSOR} MATCHES "(x86)|(X86)|(amd64)|(AMD64)")
    target_compile_definitions(project PUBLIC AE_CPU=AE_INTEL)
  endif()
```

## Acknowledgements

The original library is provided under https://www.alglib.net.
