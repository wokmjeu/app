# 声明
（你要有dev-c++,没有的去这里[link](http://www.ssoier.cn:8087/)）不喜勿喷
# 安装(以下以Win10为例)
首先打开[官网](https://code.visualstudio.com/)并下载VS Code 安装程序(Win7系统用[最后一个支持Win7的版本](https://code.visualstudio.com/updates/v1_70))

![安装程序](https://cdn.luogu.com.cn/upload/image_hosting/dtjihjyw.png)

双击及下载,其他的可以不改

![选项](https://cdn.luogu.com.cn/upload/image_hosting/o4y0g3jv.png)

这个可以根据需要勾选

![选项2](https://cdn.luogu.com.cn/upload/image_hosting/xmdsshbw.png)
# 环境变量

右键**dev-c++**,打开文件所在位置

![图片](https://cdn.luogu.com.cn/upload/image_hosting/b45vnksw.png)

将**MinGW64**移到**C盘**(可以不移，但是需要改动路径)

![图片](https://cdn.luogu.com.cn/upload/image_hosting/kg9rz386.png)

**复制路径**

![](https://cdn.luogu.com.cn/upload/image_hosting/aphxwtmk.png))

**win+r**键打开运行,输入**sysdm.cpl**

![图片](https://cdn.luogu.com.cn/upload/image_hosting/3uj5lgn7.png)

**回车**确定,点击**高级**，再点击**环境变量**

![](https://cdn.luogu.com.cn/upload/image_hosting/v9p30cfv.png)

找到Path,并点击编辑

![](https://cdn.luogu.com.cn/upload/image_hosting/jvyq1krt.png)

点击新建，把路径粘贴进去

![](https://cdn.luogu.com.cn/upload/image_hosting/09c2e586.png)

# 配置 VS Code

找到左边的5个**图标**,并点击**最后一个**,搜索**chinese**,下载并改变语言
![](https://cdn.luogu.com.cn/upload/image_hosting/3byg2zv4.png)

搜索**c++**,并安装这两个
![](https://cdn.luogu.com.cn/upload/image_hosting/n7hzpumf.png)

然后**新建一个文件夹**用于放置文件
# 附录-代码(放到.vscode中)
## 第一个
**文件名:launch.json**
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) C and C++ Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}/${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": true,
            "internalConsoleOptions": "neverOpen",
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\MinGW64\\bin\\gdb.exe",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": false
                }
            ],
            "preLaunchTask": "Compile"
        },
        {
            "name": "(gdb) 启动",
            "type": "cppdbg",
            "request": "launch",
            "program": "输入程序名称，例如 ${workspaceFolder}/a.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "/path/to/gdb",
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "将反汇编风格设置为 Intel",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

## 第二个
**文件名:settings.json**
```
{
    "C_Cpp.errorSquiggles": "disabled",
    "C_Cpp.default.compilerPath": "C:\\MinGW64\\bin\\gcc.exe",
    "files.associations": {
        "iostream": "cpp",
        "suiji": "c",
        "random": "cpp",
        "ostream": "cpp"
    }
}
```
## 第三个
**文件名:tasks.json**

```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Compile",
            "command": "C:\\MinGW64\\bin\\g++.exe",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}.exe",
                "-g",
                "-std=c++11",
                "-m64",
                "-Wall",
                "-static-libgcc",
                "-fexec-charset=GBK",
                "-D__USE_MINGW_ANSI_STDIO"
            ],
            "type": "process",
            "group": "build",
            "presentation": {
                "echo": true,
                "reveal": "always",
                "focus": false,
                "panel": "shared"
            },
            "problemMatcher": "$gcc"
        },
        {
            "type": "cppbuild",
            "label": "C/C++: g++.exe 生成活动文件",
            "command": "C:\\Program Files (x86)\\Dev-Cpp\\MinGW64\\bin\\g++.exe",
            "args": [
                "-fdiagnostics-color=always",
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "detail": "调试器生成的任务。"
        }
    ]
}
```
## 图片
### 第一个
![](https://cdn.luogu.com.cn/upload/image_hosting/zwjd7f1q.png)

### 第二个
![](https://cdn.luogu.com.cn/upload/image_hosting/8w4zqauq.png)

## 第三个
![](https://cdn.luogu.com.cn/upload/image_hosting/adv81uux.png)