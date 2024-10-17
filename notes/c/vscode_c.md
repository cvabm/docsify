# vscode配置c++环境
## minGW
- https://github.com/niXman/mingw-builds-binaries/releases
- 选`x86_64-14.2.0-release-win32-seh-msvcrt-rt_v12-rev0.7z`
- 将解压路径/bin 配置为环境变量
## 脚本配置
- `https://github.com/SDchao/AutoVsCEnv_WPF` 
- 下载解压
- 配置minGW路径`D:\software\mingw64`
    - 如果配置空路径，脚本则会自动下载
- 配置项目路径`D:\c`
- 重启vscode即可

## vscode找不到自定义头文件的方法
- 比如自定义`net.cpp`   `net.h`
- 修改 `task.json` 
 ```
    "type": "cppbuild",
    "label": "C/C++: g++ 生成活动文件",
    "command": "/usr/bin/g++",
    "args": [
        "-fdiagnostics-color=always",
        "-g",
        "${file}",
        "${fileDirname}\\/net.cpp",
        "-o",
        "${fileDirname}/${fileBasenameNoExtension}"
    ],
 ```
