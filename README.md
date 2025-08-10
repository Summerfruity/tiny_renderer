# TinyRenderer

TinyRenderer 是一个用 C++ 实现的简易软件渲染器，旨在帮助学习和理解 3D 图形渲染的基本原理。该项目实现了从 3D 模型加载、变换、光照到最终输出图像的完整渲染流程，无需依赖 OpenGL 或 DirectX 等硬件加速库。

## 目录结构

```
tinyrenderer/
├── src/
│   ├── CMakeLists.txt         # CMake 构建脚本
│   ├── geometry.cpp/h         # 向量、矩阵等几何基础类型与运算
│   ├── main.cpp               # 程序入口，渲染主流程
│   ├── model.cpp/h            # 3D 模型加载与管理
│   ├── our_gl.cpp/h           # 仿 OpenGL 的渲染管线实现
│   ├── tgaimage.cpp/h         # TGA 图像读写
│   └── build/                 # 构建输出目录
├── obj/
│   ├── *.obj                  # 示例 3D 模型文件
│   ├── *.tga                  # 贴图与法线贴图
│   └── *.jpg                  # 其他贴图资源
```

## 功能特性

- 支持 Wavefront `.obj` 格式模型加载
- 支持 TGA 格式贴图、法线贴图、镜面贴图
- 实现基础的光照模型（如 Phong、Blinn-Phong）
- 支持 z-buffer 深度测试
- 软件实现三角形光栅化
- 输出渲染结果为 TGA 图片

## 构建与运行

### 依赖

- C++11 或更高版本编译器
- [CMake](https://cmake.org/) 3.0 及以上

### 构建步骤

1. 进入源码目录：

   ```sh
   cd tinyrenderer/src
   ```

2. 创建并进入构建目录：

   ```sh
   mkdir build
   cd build
   ```

3. 运行 CMake 配置项目：

   ```sh
   cmake ..
   ```

4. 编译：

   ```sh
   make
   ```

5. 渲染模型（以 `african_head.obj` 为例）：

   ```sh
   ./render ../obj/african_head.obj
   ```

   渲染结果会输出为 `output.tga` 文件。

### 查看渲染结果

你可以使用支持 TGA 格式的图片查看器（如 GIMP、Photoshop、IrfanView 等）打开 `output.tga` 文件，或使用 ImageMagick 工具将其转换为 PNG：

```sh
convert output.tga output.png
```
<img width="847" height="827" alt="image" src="https://github.com/user-attachments/assets/1f5da79c-b442-4c0f-91f2-dc27de6860f6" />


## 主要源码说明

- [`geometry.h`](src/geometry.h)：定义了 `Vec2f`, `Vec3f`, `Matrix` 等基础几何类型及其运算。
- [`model.h`](src/model.h)：负责加载 `.obj` 模型文件和贴图。
- [`our_gl.h`](src/our_gl.h)：实现了类似 OpenGL 的渲染管线函数（如 `viewport`, `lookat`, `triangle` 等）。
- [`tgaimage.h`](src/tgaimage.h)：TGA 图片的读写实现。
- [`main.cpp`](src/main.cpp)：渲染主流程，包括模型加载、变换、光照和输出。

## 示例资源

- `obj/african_head.obj`：示例 3D 模型
- `obj/african_head_diffuse.tga`：漫反射贴图
- `obj/african_head_nm.tga`：法线贴图
- `obj/african_head_spec.tga`：高光贴图

## 参考与致谢

本项目灵感与部分实现参考自 [ssloy/tinyrenderer](https://github.com/ssloy/tinyrenderer)。

## 许可证

本项目仅用于学习和研究目的，遵循原作者的开源协议。

---

如需进一步学习 3D 渲染原理，推荐阅读 [ssloy 教程](https://github.com/ssloy/tinyrenderer/wiki)。
