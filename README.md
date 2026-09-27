# Assignment 1

## 1. System Information
```
(base) dong@dongPC:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.4 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
(base) dong@dongPC:~$ uname -r
7.0.0-34-generic
(base) dong@dongPC:~$ lscpu
架构：                       x86_64
  CPU 运行模式：             32-bit, 64-bit
  Address sizes:             46 bits physical, 48 bits virtual
  字节序：                   Little Endian
CPU:                         16
  在线 CPU 列表：            0-15
厂商 ID：                    GenuineIntel
  型号名称：                 Intel(R) Core(TM) Ultra 7 356H
    CPU 系列：               6
    型号：                   204
    每个核的线程数：         1
    每个座的核数：           16
    座：                     1
    步进：                   2
    CPU(s) scaling MHz:      54%
    CPU 最大 MHz：           4700.0000
    CPU 最小 MHz：           400.0000
    BogoMIPS：               7372.80
    标记：                   fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pg
                             e mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
                             sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm cons
                             tant_tsc art arch_perfmon bts rep_good nopl xtopolo
                             gy nonstop_tsc cpuid aperfmperf tsc_known_freq pni 
                             pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 sss
                             e3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2api
                             c movbe popcnt tsc_deadline_timer aes xsave avx f16
                             c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb 
                             ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow flexp
                             riority ept vpid ept_ad fsgsbase tsc_adjust bmi1 av
                             x2 smep bmi2 erms invpcid rdt_a rdseed adx smap clf
                             lushopt clwb intel_pt sha_ni xsaveopt xsavec xgetbv
                             1 xsaves split_lock_detect user_shstk avx_vnni lam 
                             wbnoinvd dtherm ida arat pln pts hwp hwp_notify hwp
                             _act_window hwp_epp hwp_pkg_req hfi vnmi umip pku o
                             spke waitpkg gfni vaes vpclmulqdq rdpid bus_lock_de
                             tect movdiri movdir64b fsrm md_clear serialize arch
                             _lbr ibt flush_l1d arch_capabilities
Virtualization features:     
  虚拟化：                   VT-x
Caches (sum of all):         
  L1d:                       576 KiB (16 instances)
  L1i:                       1 MiB (16 instances)
  L2:                        24 MiB (7 instances)
  L3:                        18 MiB (1 instance)
NUMA:                        
  NUMA 节点：                1
  NUMA 节点0 CPU：           0-15
Vulnerabilities:             
  Gather data sampling:      Not affected
  Ghostwrite:                Not affected
  Indirect target selection: Not affected
  Itlb multihit:             Not affected
  L1tf:                      Not affected
  Mds:                       Not affected
  Meltdown:                  Not affected
  Mmio stale data:           Not affected
  Old microcode:             Not affected
  Reg file data sampling:    Not affected
  Retbleed:                  Not affected
  Spec rstack overflow:      Not affected
  Spec store bypass:         Mitigation; Speculative Store Bypass disabled via p
                             rctl
  Spectre v1:                Mitigation; usercopy/swapgs barriers and __user poi
                             nter sanitization
  Spectre v2:                Mitigation; Enhanced / Automatic IBRS; IBPB conditi
                             onal; PBRSB-eIBRS Not affected; BHI BHI_DIS_S
  Srbds:                     Not affected
  Tsa:                       Not affected
  Tsx async abort:           Not affected
  Vmscape:                   Not affected
(base) dong@dongPC:~$ lspci | grep -Ei 'vga|3d|display'
00:02.0 VGA compatible controller: Intel Corporation Device b0a0
(base) dong@dongPC:~$ lspci -k | grep -EA3 'VGA|3D|Display'
00:02.0 VGA compatible controller: Intel Corporation Device b0a0
	Subsystem: Lenovo Device 80cf
	Kernel driver in use: xe
	Kernel modules: xe
(base) dong@dongPC:~$ echo "$XDG_SESSION_TYPE"
wayland
(base) dong@dongPC:~$ echo "$WAYLAND_DISPLAY"
wayland-0
```
```
Ubuntu:        Ubuntu 24.04.4 LTS (noble)
Kernel:        7.0.0-31-generic
CPU:           Intel(R) Core(TM) Ultra 7 356H
               x86_64，16 核，每核 1 线程，1 座
GPU:           Intel Corporation [8086:b0a0]
               Subsystem: Lenovo [17aa:80cf]
GPU 驱动:      xe（Kernel modules: xe）
图形会话:      wayland
NVIDIA Driver: N/A
CUDA Toolkit:  N/A
```



## 2. Python Project A


```bash
cd ~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1/python_A
conda create -n robocon-a python=3.10 -y
conda activate robocon-a
python --version
which python
pip install -r requirements.txt
```

环境创建成功，位置为 `/home/dong/miniforge3/envs/robocon-a`，安装的是 `python-3.10.21`。

```text
Python 3.10.21
/home/dong/miniforge3/envs/robocon-a/bin/python
```

依赖安装成功：

```text
Successfully installed numpy-1.26.4 opencv-python-4.11.0.86
```

再次执行 `pip install -r requirements.txt` 时，这两个包均已满足要求。

在 `(robocon-a)` 中运行：

```bash
python camera.py --camera 0 --output raw_capture.mp4 --width 1280 --height 720 --fps 30
```

程序打印并在退出时记录：

```text
PID:          69298
PPID:         60414
Python:       /home/dong/miniforge3/envs/robocon-a/bin/python
Python ver.:  3.10.21
Actual stream: 640x480, writer FPS=30.00
Saved raw video: .../python_A/raw_capture.mp4
Captured frames: 6341
Elapsed time:    372.7 s
Loop rate:       17.0 frame/s
```

连续运行 372.7 秒，超过 30 秒。原始视频为 `python_A/raw_capture.mp4`（mpeg4 Simple Profile，640×480，时长 3 分 31 秒）。退出方式是 `Ctrl+C`。

运行中的三个窗口：

![Project A 原始、轮廓、灰度窗口](assets/python_a/project_a_windows.png)

## 3. Process Observation

`camera.py` 启动时打印 `PID: 69298`、`PPID: 60414`。另开一个终端，先按命令名找到进程，再用 `ps` 取出各项，并和打印的 PID 核对：

```bash
pgrep -af camera.py
ps -o pid,ppid,pcpu,pmem,etime,cmd -p 69298
pstree -sp 69298
htop
```

`pgrep -af` 按完整命令行匹配 `camera.py`。下一条用这个 PID 取出父进程、CPU、内存、已运行时间和命令。`pstree -sp` 查看它和父进程的关系。

与程序打印一致的结果：

```text
PID:     69298
PPID:    60414
CMD:     python camera.py --camera 0 --output raw_capture.mp4 --width 1280 --height 720 --fps 30
CPU %:   9.7
MEM %:   1.5
ELAPSED: 372.7 s
```

CPU % 和 MEM % 是运行期间 `htop` 里该 PID 的读数。`ELAPSED` 是程序退出时打印的墙钟时间。`htop` 的 `TIME+`（1:08.51）是 CPU 时间，不是这段墙钟时间。

`htop` 里同一条命令还有多个线程（例如 69314、69318、69316、69317、69321、69323）。屏幕上方能看到整机 CPU 条、内存 `13.0G/30.9G`、任务 `252`、线程 `2642`。

![htop 中的 camera.py 与其线程](assets/process/htop.png)

## 4. Python Project B

工作目录：`ROBOCON-Vision-Assignment-1/python_B`。未修改 `pyproject.toml` 的 `requires-python`。

```bash
conda create -n robocon-b python=3.12 -y
conda activate robocon-b
python --version
which python
pip install -r requirements.txt
```

```text
Python 3.12.14
/home/dong/miniforge3/envs/robocon-b/bin/python
Successfully installed imageio-2.37.4 imageio-ffmpeg-0.6.0 numpy-2.5.3 scikit-image-0.26.0
```

在 `python_B` 目录读取 Project A 的原始视频：

```bash
python analyze_video.py \
  --input ../python_A/raw_capture.mp4 \
  --output advanced_analysis.mp4
```

输出文件为 `python_B/advanced_analysis.mp4`。编码是 H.264，分辨率 1920×480（三幅画面并排），时长 3 分 31 秒，与输入视频一致。

```text
Project A 使用的 Conda 环境：robocon-a
Python 版本：3.10.21
Project B 使用的 Conda 环境：robocon-b
Python 版本：3.12.14
为什么不能直接把两个项目当成同一个环境来完成：
Project A 要求 Python >=3.9,<3.11、NumPy >=1.26,<2.0；
Project B 要求 Python >=3.12,<3.14、NumPy >=2.0,<3.0。
Python 与 NumPy 的版本范围都没有交集，同一个环境无法同时满足两份 pyproject.toml，因此要分成 robocon-a 和 robocon-b 两个 Conda 环境。
从更广泛的意义上说，一个 Conda 环境只固定一套 Python 和库版本。两个项目要的版本互相排斥时，就各自使用一个环境，这样安装或升级其中一个项目，不会替换另一个项目已经装好的包。
```

## 5. C++ Manual Build

在 `cpp` 目录执行并成功：

```bash
g++ -std=c++17 -Iinclude -I/usr/include/eigen3 src/main.cpp src/transform.cpp $(pkg-config --cflags --libs opencv4) -o robocon
```

`-I` 的作用是什么？

`-I` 给编译器增加一个查找头文件的目录。

为什么 `transform.hpp` 不单独作为一个 cpp 文件编译？

`transform.hpp` 只有结构体和函数声明，没有函数的实现。它被 `main.cpp` 和 `transform.cpp` 用 `#include` 读进去，告诉编译器这些函数长什么样。真正的函数体在 `transform.cpp` 里，所以只编译带实现的 `.cpp` 文件。

为什么只写 `main.cpp` 往往无法得到完整程序？

`main.cpp` 调用的函数在 `transform.cpp`中才有定义。只编译 `main.cpp` 时，链接阶段找不到这两个函数的本体，程序不完整。

编译成功后产生的文件是什么？

当前目录下的可执行文件 `robocon`。

## 6. CMake Build
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
cmake_minimum_required(VERSION 3.16)
project(robocon)
add_executable(robocon src/main.cpp src/transform.cpp) 
find_package(OpenCV REQUIRED)
find_package(Eigen3 REQUIRED)
target_include_directories(robocon PRIVATE include)
target_link_libraries(robocon PRIVATE ${OpenCV_LIBS} Eigen3::Eigen)


```text
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ cd ~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1/cpp
cmake -S . -B build
cmake --build build
./build/robocon ../python_A/raw_capture.mp4
-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found OpenCV: /usr (found version "4.6.0") 
-- Configuring done (0.3s)
-- Generating done (0.0s)
-- Build files have been written to: /home/dong/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1/cpp/build
[ 33%] Building CXX object CMakeFiles/robocon.dir/src/main.cpp.o
[ 66%] Building CXX object CMakeFiles/robocon.dir/src/transform.cpp.o
[100%] Linking CXX executable robocon
[100%] Built target robocon
Input: ../python_A/raw_capture.mp4
Output: cpp_processed.mp4
Frames: 6341
Mean scene luma: 66.7655
Panels: original | Otsu binary | Canny edges
```


```
手工 g++ 命令和 CMake 的关系是什么？


手工执行的 `g++` 是真正编译代码的命令。CMake 读取 `CMakeLists.txt`，按照其逻辑生成等价的命令。源文件变多时，每个目标在 CMake 里登记自己的源文件、头文件目录和要链接的库，不必把所有参数写进同一条 `g++` 命令。
```
## 7. Git / GitHub

记录实际执行过的 `git status`、`git add`、`git commit`、`git branch`、`git switch`、`git push`、`git log --oneline --graph --all`。

```text
git restore --staged cpp/cpp_task
git commit -m "版本1"
[master ff939e9] 版本1
 6 files changed, 208 insertions(+), 6 deletions(-)
 create mode 100644 cmakelists.txt
 create mode 100644 cpp/README.md
 create mode 100644 cpp/include/transform.hpp
 create mode 100644 cpp/src/main.cpp
 create mode 100644 cpp/src/transform.cpp

(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git switch -c cmake-build
切换到一个新分支 'cmake-build'
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git branch
* cmake-build
  master
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git add .
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git restore --staged cpp/robocon
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git commit
终止提交因为提交说明为空。
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git commit -m "版本2"
[cmake-build 512f6c6] 版本2
 3 files changed, 65 insertions(+), 10 deletions(-)
 delete mode 100644 cmakelists.txt
 create mode 100644 cpp/CMakeLists.txt
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git switch master
git merge cmake-build
切换到分支 'master'
更新 ff939e9..512f6c6
Fast-forward
 README.md          | 65 ++++++++++++++++++++++++++++++++++++++++++++++++------
 cmakelists.txt     |  3 ---
 cpp/CMakeLists.txt |  7 ++++++
 3 files changed, 65 insertions(+), 10 deletions(-)
 delete mode 100644 cmakelists.txt
 create mode 100644 cpp/CMakeLists.txt
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git add .
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git restore --staged cpp/robocon
(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git commit -m "版本3"
[master f402292] 版本3
 1 file changed, 36 insertions(+), 12 deletions(-)
 ssignment-1$ git status
位于分支 master
无文件要提交，干净的工作区

(base) dong@dongPC:~/robocon/ROBOCON-Vision-Assignment1-Starter/ROBOCON-Vision-Assignment-1$ git log --oneline --graph --all

* f402292 版本4
* 512f6c6 (cmake-build) 版本3
* ff939e9 版本2
* 447c25b 记录系统信息与 Python A/B 的运行结果
```

## 8. Problems and Notes
```
我的电脑有独显，也曾经装过驱动，可以识别显卡，第一部分没有识别是因为我为了续航开的纯集显
最后几次git提交我没有记录上
并未实际用上git branch，只是尝试了一下
桌面播放器打不开 mp4v
解决：安装对应的播放器
CMake与g++语法不清楚
C++编译过程不清楚
解决：网络资源，询问ai
```
