find_package(KernelHeader REQUIRED)
set(KERNEL_MODULE_NAME "hello")

# ./src/kernel
add_definitions(-D__KERNEL__ -DMODULE)
set(KERNEL_MODULE_FILE_NAME "${KERNEL_MODULE_NAME}.ko")

# add header to include path
include_directories(KERNEL_HEADER_INCLUDE)

# configure the compile command
set(KBUILD_CMD $(MAKE) -C ${KERNEL_SOURCE_DIR} M=${CMAKE_CURRENT_BINARY_DIR} src=${CMAKE_CURRENT_SOURCE_DIR} modules)
message(STATUS "current binary dir: ${CMAKE_CURRENT_BINARY_DIR}")
message(STATUS "current source dir: ${CMAKE_CURRENT_SOURCE_DIR}")

# Generate the Kbuild file through cmake.
FILE(WRITE ${CMAKE_CURRENT_SOURCE_DIR}/Kbuild "obj-m := hello.o")

add_custom_command(OUTPUT ${KERNEL_MODULE_FILE_NAME}
    COMMAND ${KBUILD_CMD}
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    DEPENDS hello.c VERBATIM
)

add_custom_target(driver ALL DEPENDS ${KERNEL_MODULE_FILE_NAME})