# Project-template
my project template with CMake

for kernel module, use the following `c_cpp_properties.json`
```json
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "/usr/src/linux-headers-5.15.90.1-microsoft-standard-WSL2/arch/x86/include/generated",
                "/usr/src/linux-headers-5.15.90.1-microsoft-standard-WSL2/arch/x86/include",
                "/usr/src/linux-headers-5.15.90.1-microsoft-standard-WSL2/include",
                "${workspaceFolder}/**"
            ],
            "defines": [
                "__GNUC__",
                "__KERNEL__=1",
                "MODULE=1"
            ],
            "compilerPath": "/usr/bin/clang",
            "intelliSenseMode": "linux-clang-x64",
            "compileCommands": "${workspaceFolder}/build/compile_commands.json",
            "cStandard": "c17",
            "cppStandard": "c++17"
        }
    ],
    "version": 4
}
```