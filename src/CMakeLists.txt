find_package(Boost 1.36.0 REQUIRED COMPONENTS thread system serialization)

if(Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
    link_directories(${Boost_LIBRARY_DIRS})
endif()

include_directories(${Boost_INCLUDE_DIRS} ../include)
link_directories(${Boost_LIBRARY_DIRS} ../lib)


# set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_BUILD_TYPE "Debug")
set(CMAKE_C_FLAGS_DEBUG "-Wall -g -ggdb") 
set(CMAKE_C_FLAGS_RELEASE "-O3 -Wall")
set(CMAKE_CXX_FLAGS_DEBUG "-Wall -g -ggdb -fsanitize=address -O0 -fno-omit-frame-pointer")
#set(CMAKE_CXX_FLAGS_DEBUG "-Wall -g -ggdb") # for gdb, for valgrind
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall")

SET (CMAKE_C_COMPILER "/usr/bin/clang")
SET (CMAKE_CXX_COMPILER "/usr/bin/clang++")
SET (CMAKE_AR "/usr/bin/llvm-ar")
SET (CMAKE_LINKER "/usr/bin/llvm-ld")
SET (CMAKE_NM "/usr/bin/llvm-nm")
SET (CMAKE_OBJDUMP "/usr/bin/llvm-objdump")
SET (CMAKE_RANLIB "/usr/bin/llvm-ranlib")

add_subdirectory(app)