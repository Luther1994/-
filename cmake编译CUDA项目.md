# 解决CMake 编译出错：“No CUDA toolset found”

## 问题描述

"CMake Error: No CUDA toolset found"报错，尽管已经安装了CUDA，但CMake检测不到CUDA工具集

## 解决方案

### 步骤1: 确认CUDA安装

1. **确认CUDA安装路径**:
    - 确保已经正确安装了CUDA工具包。默认情况下，CUDA安装在`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA-12.5(你安装的版本号)`下。
    - 查看CUDA的版本，可以通过命令行输入`nvcc --version`来查看。

2. **确认CUDA环境变量**:
    - 确认`PATH`环境变量包含了CUDA的bin目录，例如`C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA-12.5\bin`
    - 
### 步骤2: 复制CUDA集成文件

1. **确定CUDA安装路径**:
    - 如果你不确定CUDA的确切安装路径，可以在命令行中输入`where nvcc`来查找。

2. **复制CUDA集成文件**:
    - 寻找CUDA安装路径下的`extras\visual_studio_integration\MSBuildExtensions`文件夹。例如：
      ```
      C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.5\extras\visual_studio_integration\MSBuildExtensions
      ```

3. **确定Visual Studio安装路径**:
    - 找到自己安装VS的安装路径下的BuildCustomizations目录。例如：
    - `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\BuildCustomizations`

4. **复制文件**:
    - 将MSBuildExtension路径下的所有文件复制到Visual Studio的`BuildCustomizations`目录下。分别为：
      ```
        CUDA 12.5.props
        CUDA 12.5.targets
        CUDA 12.5.xml
        Nvda.Build.CudaTasks.v12.5.dll
      ```

## 注意事项

- 确保Visual Studio版本和CUDA版本兼容。
- 根据实际情况调整上述路径中的版本号。
- VS2022只支持CUDA12.5及以上版本。使用11.8可能会报出来一堆乱码。
