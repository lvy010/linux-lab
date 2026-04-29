# linux-lab

> Linux 操作系统学习与实验的聚合仓库——读书笔记、内核探索、专栏配套代码，一站式整合。

这个仓库记录了我在 Linux 系统方向的完整学习路径：从 OSTEP 经典教材的读书笔记与演示代码，到 Linux 内核机制的动手实验，再到 50 篇技术博文的配套源码。三部分内容均为原创整理。

目前我的工作重心已转向 AI 方向（见 [AI-exploration](https://github.com/lvy010/AI-exploration)），但 Linux 系统层面的积累——进程调度、IPC、网络协议栈、设备驱动——对理解 AI 基础设施（GPU 调度、高性能通信、内核态优化）仍然是不可替代的基础。

## 仓库结构

```text
linux-lab/
├── csapp_os_code/    # OSTEP 读书笔记与演示代码
├── linux-core/       # Linux 内核机制实验项目
└── linux-study/      # 技术专栏配套代码（~50 篇）
```

## 一、OSTEP 读书笔记与演示代码（`csapp_os_code/`）

基于 *Operating Systems: Three Easy Pieces* 的学习笔记，每个子目录对应一个操作系统概念的可运行演示。

| 主题 | 子目录 | 说明 |
|------|--------|------|
| 虚拟化 | `kvm/` | KVM 虚拟机最小实现 |
| 并发 | `mandelbrot/` `mandelbrot-cu/` | Mandelbrot 渲染（OpenMP / CUDA） |
| 并发 | `lockdep/` `tsan/` | 锁依赖追踪 / ThreadSanitizer 竞态检测 |
| 持久化 | `overlay/` | OverlayFS 分层文件系统演示 |
| 安全 | `security/` | 缓冲区溢出、SUID 提权、登录模拟 |
| 设备驱动 | `ioctl/` `launcher/` | ioctl 接口 / 用户态-驱动配对 |
| 资源隔离 | `cgroups/` | cgroups 观测脚本 |
| 嵌入式 | `NimBLE-蓝牙/` | 蓝牙事件处理、定时器、智能指针 |
| 其他 | `litenes/` | NES 模拟器（C 实现） |
| 其他 | `go-examples/` | Go 并发：生产者-消费者、Fibonacci |

笔记大纲覆盖 OSTEP 三大部分：虚拟化（进程/调度/多核）、并发（线程/锁/信号量/管程）、持久化（文件系统/日志/崩溃一致性）。

## 二、Linux 内核机制实验（`linux-core/`）

三个独立的深度实验项目，每个都有完整的 README 文档、编译脚本和测试用例。

| 项目 | 说明 | 涵盖内容 |
|------|------|----------|
| `ipc_test/` | IPC 全机制学习项目 | 管道、消息队列、共享内存、信号量、Socket |
| `tun_test/` | TUN 设备网络工具包 | 虚拟网卡、路由转发、防火墙规则、VPN Server |
| `smart_pointer_lab/` | C++ 智能指针实验 | shared_ptr / unique_ptr / weak_ptr、循环引用、线程安全 |

## 三、技术专栏配套代码（`linux-study/`）

对应 CSDN 专栏 [「Linux OS + 网络」](https://blog.csdn.net/2301_80171004/category_12699620.html) 的 ~50 篇文章，按日期组织。每个目录包含文章中的完整可运行代码和对应博文链接。

学习路径覆盖：

| 阶段 | 时间 | 主题 |
|------|------|------|
| Linux 基础 | 2024.06 | 命令行、权限、Vim、Makefile、Git |
| 进程与线程 | 2024.06 – 08 | 进程状态、fork、exec、POSIX 线程、锁、死锁、生产者-消费者 |
| 网络编程 | 2024.08 – 10 | Socket、UDP/TCP、HTTP/HTTPS、序列化、epoll |
| 协议深入 | 2024.10 – 2025.05 | TCP 滑动窗口/拥塞控制、IP 分片/路由、ARP/DNS/ICMP、NAT、IO 模型 |
| 工具与实践 | 2024.12 – 2025.01 | perf 性能分析、Ubuntu 双系统安装 |

代码类型包括：简易 Shell、HTTP 服务器、TCP 服务器、线程池、UDP 聊天系统、epoll 服务器等。

## 技术栈

- **语言**：C / C++ 为主，辅以 Python、Go、Java
- **构建**：Make / CMake
- **环境**：Linux（Ubuntu），部分项目需要 root 权限（TUN、cgroups、KVM）

## 使用方式

各子目录均为独立项目，进入对应目录查看 README 即可：

```bash
cd csapp_os_code/kvm && make && ./kvm-demo
cd linux-core/ipc_test && bash compile_all.sh
cd linux-study/24-09-28-linux && make && ./http_server
```

## 许可协议

MIT（具体以子目录内说明为准）

