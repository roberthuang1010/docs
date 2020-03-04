```eval_rst
:github_url: https://github.com/littlevgl/docs/blob/master/zh-CN/get-started/pc-simulator.md
```
# PC模拟器

你可以 **仅使用PC机** 去测试 LittlevGL （即无需任何开发板）。 LittlevGL可以运行在一个任何人都可以编写及测试实际 LittlevGL 应用程序的模拟环境中。
PC模拟器有如下优点：
- 硬件独立 - 写一次代码，可在PC模拟器上运行及观测运行结果
- 跨平台 - 任意Windows, Linux 或 OSX 平台机器都可以运行PC模拟器
- 可移植性 - 编写的代码可移植, 意味着编写的代码可轻松复制到嵌入式硬件中
- 易于验证 - 每一个用户都有一个通用平台，使得平台模拟器在查找程序漏洞方面非常有用。在模拟器中重现一个漏洞并在[论坛](https://forum.littlevgl.com) 中发布代码片段是个不错的点子.


## 选择一个IDE
模拟器被移植到多个IDE(集成开发环境)中。选择你最喜欢的IDE,阅读 GitHub 里面的相关IDE的 README 文档, 下载项目文件并将其导入到IDE中。

```eval_rst
.. raw:: html

  <table style="width:100%">
  <thead>
  <tr>
  <th>Eclipse</th>
  <th>CodeBlocks</th>
  <th>Visual Studio</th>
  <th>PlatformIO</th>
  <th>Qt Creator</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><a href="https://github.com/littlevgl/pc_simulator_sdl_eclipse"><img src="https://littlevgl.com/logo/ide/eclipse.jpg"></a> </td>
  <td><a href="https://github.com/littlevgl/pc_simulator_win_codeblocks"><img src="https://littlevgl.com/logo/ide/codeblocks.jpg"></a></td>
  <td><a href="https://github.com/littlevgl/visual_studio_2017_sdl_x64"><img src="https://littlevgl.com/logo/ide/visualstudio.jpg"></a></td>
  <td><a href="https://github.com/littlevgl/pc_simulator_sdl_platformio"><img src="https://littlevgl.com/logo/ide/platformio.jpg"></a></td>
  <td><a href="https://blog.littlevgl.com/2019-01-03/qt-creator"><img src="https://littlevgl.com/logo/ide/qtcreator.jpg"> </a></td>
  </tr>

  <tr>
  <td>Cross-platform<br>with SDL 
  </td><td>Native Windows  </td>
  <td>Cross-platform<br>with SDL  </td>
  <td>Cross-platform<br>with SDL </td>
  <td>Cross-platform<br>with SDL  </td>
  </tr>
  </tbody></table>
```

可以用任意IDE去开发程序，为了简便起见，本教程重点介绍 Eclipse CDT 的配置。下一节将更加详细地介绍 Eclipse CDT 的设置。
**注: 如果你用Windows操作系统, 使用Visual Studio 或 CodeBlocks会更好一些, 他们不需要额外配置即可直接使用.**

## 配置 Eclipse CDT

### 安装 Eclipse CDT

[Eclipse CDT](https://eclipse.org/cdt/) is a C/C++ IDE.

Eclipse 是基于Java的软件，因此请确保 **Java 运行时环境（JRE）** 已经安装在你的系统上

在类Debian发行版上运行 (如：Ubuntu): `sudo apt-get install default-jre`

Note: If you are using other distros, then please refer and install 'Java Runtime Environment' suitable to your distro.

You can download Eclipse's CDT from: [https://www.eclipse.org/cdt/downloads.php](https://www.eclipse.org/cdt/downloads.php). Start the installer and choose *Eclipse CDT* from the list.

### 安装 SDL 2

PC模拟器使用  [SDL 2](https://www.libsdl.org/download-2.0.php) 跨平台库来模拟 TFT 显示设备和触摸板。 

#### Linux
在 **Linux**  上你可以通过终端简单的安装SDL2：

1. 找到当前的SDL2版本: `apt-cache search libsdl2 (例如 libsdl2-2.0-0)`
2. 安装 SDL2: `sudo apt-get install libsdl2-2.0-0` (替代你找到的版本)
3. 安装SDL2开发包: `sudo apt-get install libsdl2-dev`
4. 如果基本编译库build essentials尚未安装: `sudo apt-get install build-essential`

#### Windows
If you are using **Windows** firstly you need to install MinGW ([64 bit version](http://mingw-w64.org/doku.php/download)). After installing MinGW, do the following steps to add SDL2:

1. 下载SDL的开发库   
前往 [https://www.libsdl.org/download-2.0.php](https://www.libsdl.org/download-2.0.php) 并 _下载库: SDL2-devel-2.0.5-mingw.tar.gz_
2. 解压并前往 _x86_64-w64-mingw32_ 文件夹(64 位的MinGW) 或 _i686-w64-mingw32_ ( 32 位的MinGW)
3. 复制 _..._mingw32/include/SDL2_ 文件夹到 _C:/MinGW/.../x86_64-w64-mingw32/include_
4. 复制_..._mingw32/lib/_ 中的内容到 _C:/MinGW/.../x86_64-w64-mingw32/lib_
5. 复制_..._mingw32/bin/SDL2.dll_ 到_{eclipse_worksapce}/pc_simulator/Debug/_，请在Eclipse完成安装后执行

Note: If you are using **Microsoft Visual Studio** instead of Eclipse then you don't have to install MinGW. 

#### OSX
你可以容易的通过brew在 **OSX** 上安装SDL2 ：`brew install sdl2`

If something is not working, then please refer [this tutorial](http://lazyfoo.net/tutorials/SDL/01_hello_SDL/index.php) to get started with SDL.

### 预配置项目

A pre-configured graphics library project (based on the latest release) is always available to get started easily. 
You can find the latest one on [GitHub](https://github.com/littlevgl/proj_pc) or on the [Download](https://littlevgl.com/download) page. 
(Please note that, the project is configured for Eclipse CDT). 

### 添加预配置项目到Eclipse CDT

Run Eclipse CDT. It will show a dialogue about the **workspace path**. Before accepting the path, check that path and copy (and unzip) the downloaded pre-configured project there. After that, you can accept the workspace path. Of course you can modify this path but, in that case copy the project to the corresponding location.

关闭开始窗口并前往 **File-&gt;Import** 选择 **General-&gt;Existing project into Workspace**. **选择项目根目录** 并点击 **Finish**

在 **Windows** 你必须做这两件额外的事：

- 复制 **SDL2.dll** 到项目的Debug目录
- 右击项目的 -&gt; Project properties -&gt; C/C++ Build -&gt; Settings -&gt; Libraries -&gt; Add ... 并在 _mingw32_ 上添加 SDLmain 和 SDL。 (这个顺序非常重要: mingw32, SDLmain, SDL)

### 编译并运行

Now you are ready to run the LittlevGL Graphics Library on your PC. Click on the Hammer Icon on the top menu bar to Build the project. If you have done everything right, then you will not get any errors. Note that on some systems additional steps might be required to "see" SDL 2 from Eclipse but, in most of cases the configurations in the downloaded project is enough.

After a success build, click on the Play button on the top menu bar to run the project. Now a window should appear in the middle of your screen.

现在所有东西已经准备好，你可以开始在你PC上实践使用LittlevGL图形库了。
