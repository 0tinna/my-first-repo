太好了，我将为你生成一套系统性的 DevOps 学习路径，从 Linux 基础出发，逐步深入到 Docker、Kubernetes 和 OpenStack，每一步都配有详细讲解、代码示例、注释说明和练习任务。内容将以 Markdown 格式组织，按照你每周可投入约 15 小时的节奏，结构清晰，便于系统学习并适配实际运维需求。我会尽快准备好初稿给你审核。
零基础云原生 DevOps 技术栈学习指南
=====================

本指南旨在为零基础学习者提供一套完整的 DevOps 学习体系，涵盖 **Linux → Docker → Kubernetes → OpenStack** 的学习路线，逐步掌握云原生运维技术栈。内容按章节循序渐进，每章从基础讲起并逐步深入，每个知识点附有通俗易懂的说明、示例代码和命令行演示，并提供练习案例。我们建议以每周约 15 小时的学习节奏，坚持数月，逐步夯实技能。在后期 Kubernetes 和 OpenStack 章节中，我们将侧重实战，包括部署、调试、日志查看和故障排除等真实运维任务，强化读者的命令行操作能力、自动化脚本编写（Bash/Python）、配置管理与监控工具使用等技能。此指南适合作为转型云计算运维工程师的长期学习规划，也可用作技术博客或 GitHub 项目文档。
学习规划概述
------

在开始具体技术内容之前，我们先制定一个宏观的学习计划，并介绍一些学习方法：

* **分阶段学习路线：** 建议前 4 周集中学习 Linux 基础和简单脚本编程，再用约 2 周学习 Docker 容器技术；随后用 4-6 周深入 Kubernetes 基础与实战；最后 4-6 周学习 OpenStack 云平台及综合实践。这个进度可根据个人情况调整，但应确保先扎实掌握 Linux，再逐步推进到容器和云平台领域。

* **项目驱动实践：** 每当学完一个知识点，尝试将其应用到一个小项目中。例如，在学完 Linux 和 Docker 后，可以尝试将一个简单应用打包为容器；学习完 Kubernetes 后，将该应用部署到 K8s 集群中；OpenStack 学习后，可尝试在 OpenStack 上部署应用或 Kubernetes 集群。通过项目实践将零散的知识串联起来，加深理解，也为将来构建作品集奠定基础。

* **定期总结分享：** 建议每学完一个阶段，就撰写总结笔记或博客，对所学内容进行整理和反思。这不仅加深记忆，也培养文档编写能力。如果用英文撰写技术笔记，更能提升专业影响力。

* **关注社区与求助：** 主动加入相关开源社区（如 Linux 基金会、Docker 社区、Kubernetes & OpenStack 官方社区等），订阅博客或公众号，了解行业最新动态。遇到问题时学会阅读官方文档和社区 Q&A，在实践中培养自主解决问题的能力。

接下来，我们将按章节展开详细内容。
第一部分：Linux 操作系统基础
-----------------

作为云原生和 DevOps 技术的基石，Linux 是必不可少的第一步。**大多数服务器和云平台都运行在 Linux 上**，熟练掌握 Linux 有助于我们对系统行为、自动化和部署有深度控制 ([Devops and Linux Tutorial | GeeksforGeeks](https://www.geeksforgeeks.org/devops-and-linux-tutorial/#:~:text=Before%20starting%20with%20DevOps%2C%20learning,changes%20and%20manage%20version%20control))。本章节针对零基础用户，从操作系统概念到常用命令、脚本和故障排查，逐步介绍 Linux 运维必须掌握的知识点。

### 1.1 Linux 简介与环境准备

Linux 是一种自由开源的操作系统，具有稳定、安全、灵活和高性能的特点 ([Devops and Linux Tutorial | GeeksforGeeks](https://www.geeksforgeeks.org/devops-and-linux-tutorial/#:~:text=Linux%20is%20a%20free%2C%20open,stability%2C%20security%2C%20flexibility%2C%20and%20performance))。DevOps 工程师常用的发行版包括 **Ubuntu**、**CentOS/RHEL**、**Debian** 等，它们在核心上相同（都使用 Linux 内核），但包管理器和预装软件有所不同。对于初学者，Ubuntu 是一个友好的选择，因为其社区庞大、文档丰富；CentOS/RHEL 则在企业环境中常见。

**如何获得 Linux 环境？** 如果你的电脑已安装 Windows 或 macOS，不妨通过以下方式获取一个 Linux 实践环境：

* **虚拟机**：使用 VirtualBox、VMware 等虚拟机软件，在本机上安装 Ubuntu 或 CentOS 镜像。这样可以在不影响现有系统的情况下体验完整的 Linux 环境。

* **双系统或WSL**：将 Linux 和现有系统双启动，或在 Windows 10+ 上启用 Windows Subsystem for Linux (WSL2) 来运行 Ubuntu 子系统，无需额外虚拟机。

* **云服务器**：申请云厂商提供的免费试用云主机（如 AWS、Azure、阿里云等的入门款），通过 SSH 远程连接练习真实的 Linux 服务器环境。

准备好环境后，就可以开始熟悉 Linux 的基础知识和操作。

### 1.2 操作系统与Linux基础概念

在深入命令实践前，我们先了解操作系统和 Linux 的基本概念：

* **操作系统内核 (Kernel)：** Linux 的核心是内核，它负责管理硬件资源、进程调度、内存和设备驱动等底层功能。Linux 内核提供了对上层应用的抽象，使开发者不必直接操作硬件。

* **发行版 (Distribution)：** Linux 内核加上一系列软件包和管理工具，就构成了各种发行版。不同发行版如 Ubuntu、CentOS 只是在软件选型和默认配置上略有差异，但常用命令和文件系统结构大同小异。

* **Shell 与终端：** Shell 是用户与操作系统交互的命令解释器。常见的 shell 有 Bash（大多数 Linux 默认）和 Zsh 等。我们通过“终端（Terminal）”输入 shell 命令来控制系统。

* **文件系统层次：** Linux 将所有内容组织为树状的文件系统结构，根目录 `/` 是起点。常见子目录有 `/home`（用户主目录）、`/etc`（配置文件）、`/var`（可变数据，如日志）、`/usr`（用户程序和库）等。理解这些目录的用途有助于定位文件和配置。

以上概念有助于理解 Linux 的运作原理，但学习操作系统更重要的是实践。下面我们将通过示例命令，熟悉 Linux 常用操作。

### 1.3 文件和目录操作

Linux 是类 UNIX 操作系统，提供了丰富的命令行工具来管理文件和目录。以下是一些必须掌握的基本命令：

* `pwd`（print working directory）：显示当前所在的工作目录路径。

* `ls`（list）：列出目录内容。常用参数：
  
  * `-a`：显示所有文件（包括以 `.` 开头的隐藏文件）。
  
  * `-l`：使用长格式显示，包含权限、所有者、大小、修改时间等信息。
  
  * `-h`：配合 `-l`，以人类可读的单位显示文件大小（例如 KB、MB）。

* `cd`（change directory）：切换当前工作目录。用法：`cd 目录路径`。例如 `cd /etc` 进入系统配置目录，`cd ~` 或 `cd` 返回当前用户的主目录。

* `mkdir`（make directory）：创建新目录。加参数 `-p` 可递归创建多级目录。

* `touch`：创建空文件或更新文件的时间戳。例如 `touch test.txt` 会生成一个空的 `test.txt` 文件。

* `cp`（copy）：复制文件或目录。用法：`cp 源 目标`。加 `-r` 递归复制整个目录。

* `mv`（move）：移动或重命名文件/目录。用法类似 `cp`。例如 `mv old.txt new.txt` 将文件改名，`mv file.txt /tmp/` 移动文件到 `/tmp` 目录。

* `rm`（remove）：删除文件。`rm -r` 可递归删除目录及其中内容，`rm -f` 强制删除不提示。**注意：`rm` 无法恢复，被删除的文件无法轻易找回，使用时需谨慎。**

* `cat`（concatenate）：打印文件内容到终端（一次性输出全文）。

* `less`：分页查看文件内容，支持上下滚动，是查看长文件的利器。按 `q` 退出查看。

下面通过一个示例，演示常用文件操作命令：
    # 查看当前所在路径
    $ pwd
    /home/student

    # 列出当前目录下所有文件（包括隐藏文件），以详细长格式显示
    $ ls -alh
    drwxr-xr-x 2 student student 4.0K Apr 22 09:00 .
    drwxr-xr-x 5 root    root    4.0K Apr 22 08:59 ..
    -rw-r--r-- 1 student student    0 Apr 22 09:00 .bash_history
    -rw-r--r-- 1 student student    0 Apr 22 09:00 test.txt

    # 创建一个新目录并进入该目录
    $ mkdir -p projects/demo
    $ cd projects/demo

    # 在当前目录创建两个新文件
    $ touch file1.txt file2.txt

    # 将 file1.txt 重命名为 project.txt
    $ mv file1.txt project.txt

    # 将 project.txt 复制一份为 backup.txt
    $ cp project.txt backup.txt

    # 查看当前目录内容
    $ ls -l
    -rw-r--r-- 1 student student 0 Apr 22 09:01 backup.txt
    -rw-r--r-- 1 student student 0 Apr 22 09:01 file2.txt
    -rw-r--r-- 1 student student 0 Apr 22 09:01 project.txt

    # 删除 file2.txt
    $ rm file2.txt

上例中，我们演示了查看路径、列出文件、创建目录和文件、复制移动和删除等操作。命令行的灵活性很高，比如 `ls` 可以组合多个参数一起使用（如 `ls -alh` 同时应用了 `-a/-l/-h`）。

**练习：**

* 使用 `ls` 列出你的主目录（`~`）下的所有文件，尝试不同参数组合查看输出差异，如 `ls -l` 和 `ls -lh`。

* 尝试创建一个多级目录（例如 `test/dir1/dir2`），在最深的目录中创建一些文件，然后练习复制整个目录到另一个位置，最后删除该目录。

* 用 `cat` 或 `less` 查看系统中的文本文件，例如 `/etc/os-release`（包含系统发行版信息）或 `/etc/passwd`（用户账户信息）。

通过以上练习，应熟悉基本的文件系统导航和管理操作。这些是进行任何进一步开发和运维的前提。

### 1.4 用户、用户组与权限管理

Linux 是多用户、多任务系统，不同用户和进程通过权限机制隔离，保证系统安全。理解文件权限和用户管理对于运维非常重要。

**1.4.1 用户和用户组：** 每个 Linux 用户都有唯一的用户名和用户ID (UID)，每个用户属于一个或多个用户组 (Group)。用户组用来方便地管理一组用户的权限。例如，系统可能有一个 `developers` 组，赋予对某些开发资源的访问权限，只需将相关用户加入该组即可。

常用的用户管理命令：

* `whoami`：查看当前登录用户。

* `sudo`：以超级用户（root）权限执行命令。很多发行版默认普通用户无法执行管理操作，需要在命令前加 `sudo` 提升权限。

* `adduser` / `useradd`：添加新用户。（`adduser` 更易用一些，会交互式创建用户目录等）。

* `passwd`：修改用户密码。

* `su [用户名]`：切换用户身份（`su -` 切换到 root 用户）。

* `usermod`：修改用户属性（比如 `usermod -aG group user` 将用户加入某用户组）。

* `id [用户名]`：查看用户所属的UID和组。

**1.4.2 文件权限：** Linux 文件权限采用 **owner（所有者）- group（所属组）- others（其他用户）** 三类主体，每类主体分别有读取 (r)、写入 (w)、执行 (x) 三种权限。用 `ls -l` 可以查看文件权限，如：
    -rwxr-xr-- 1 alice developers  4096 Apr 22 09:00 script.sh

最左侧的 10 个字符表示类型和权限：第一个字符 `-` 表示这是普通文件（`d` 表示目录）；接下来的每组三个字符表示 **所有者**、**所属组**、**其他人** 的权限。如上例：

* 所有者 (alice) 的权限是 `rwx`，即可读、可写、可执行。

* 所属组 (developers) 的权限是 `r-x`，即可读、可执行，不能写。

* 其他用户的权限是 `r--`，即只读。

**修改权限和所属：**

* `chmod`（change mode）：修改文件或目录的权限。有两种用法：
  
  1. **符号法：** 使用 `u`（所有者）, `g`（组）, `o`（其他）, `a`（全体）；`+` 增加权限, `-` 移除权限, `=` 设置权限。比如：`chmod u+x script.sh` 给文件所有者增加执行权限；`chmod go-w file.txt` 移除组和其他用户的写权限。
  
  2. **八进制数字法：** 用一个三位八进制数表示权限，每位分别对应 owner、group、others。`r=4,w=2,x=1`，相加表示组合权限。如 `7` 表示 r+w+x，`5` 表示 r+x。常见如 `chmod 755 mydir`，将目录权限设置为 `rwxr-xr-x`（所有者7，组5，其他5）；`chmod 644 file.txt` 结果为 `rw-r--r--`。

* `chown`（change owner）：改变文件的所有者和组。用法：`chown [新所有者][:新组] 文件名`。例如 `sudo chown root:root /var/log/syslog` 将 syslog 文件的所有者和组都改为 root。

* `chgrp`：单独改变文件的所属组（功能上相当于 `chown :新组 文件`）。

**示例：**
    # 假设当前用户为 student，新建一个文件
    $ echo "Hello" > hello.sh

    # 查看文件权限和所有者
    $ ls -l hello.sh
    -rw-r--r-- 1 student student 6 Apr 22 09:30 hello.sh

    # 当前只有 rw- 权限，没有执行权限，尝试直接执行会失败
    $ ./hello.sh
    bash: ./hello.sh: Permission denied

    # 为所有者添加执行权限，使其变为 rwx
    $ chmod u+x hello.sh
    $ ls -l hello.sh
    -rwxr--r-- 1 student student 6 Apr 22 09:30 hello.sh

    # 再次执行（现在作为脚本执行，因为有了可执行权限）
    $ ./hello.sh
    Hello

    # 将文件的所属用户改为 root（需有权限，普通用户要用 sudo）
    $ sudo chown root:root hello.sh
    $ ls -l hello.sh
    -rwxr--r-- 1 root root 6 Apr 22 09:30 hello.sh

上例展示了如何查看和修改文件权限，以及权限不足时系统如何限制操作。例如最初 `hello.sh` 没有执行权限，尝试运行会被拒绝；添加执行权限后即可运行。修改文件拥有者通常需要超级用户权限（sudo）。

**练习：**

* 创建一个文件，尝试设置不同的权限组合（如 600、644、755、777 等），然后用不同用户角色去读取/写入，观察权限带来的限制。

* 新建一个用户（可在虚拟机内操作），用该用户登录，测试访问另一个用户文件时的情况，加深对 owner/others 权限区别的理解。

* 用 `chmod` 的符号法给某个脚本添加执行权限，用数字法将一个目录权限设为所有人完全访问（777），再改回更安全的权限。

**1.4.3 sudo 与 root：** Linux 中 `root` 用户是超级管理员，拥有对系统的一切操作权限。出于安全考虑，日常操作尽量不直接使用 root，而是在需要时通过 `sudo` 提升权限执行单条命令。例如 `sudo nano /etc/hosts` 用管理员权限编辑系统 hosts 文件。第一次使用 `sudo` 可能会提示输入当前用户密码（验证你有使用 sudo 的权限）。

通常，管理员会将需要提权的用户加入 `sudoers` 列表（在 Ubuntu 上，安装时第一个用户默认有 sudo 权限）。管理 sudo 权限可以编辑 `/etc/sudoers`（建议使用 `visudo` 工具编辑确保语法正确）。

通过对用户和权限的学习，我们可以在保证系统安全的前提下，灵活地管理资源访问和操作权限，这是运维管理的重要内容。

### 1.5 软件包管理与系统更新

Linux 系统的软件安装和更新通常通过包管理器完成，不同发行版使用不同的包管理工具：

* Debian 系及 Ubuntu 使用 **APT**（Advanced Package Tool），常用命令：`apt update` 更新软件源索引，`apt install <包名>` 安装软件包，`apt remove <包名>` 卸载包，`apt upgrade` 更新已安装的软件。

* RHEL/CentOS 使用 **YUM**（现新版为 **DNF**），用法类似：`yum update`，`yum install <包名>`，`yum remove <包名>` 等。

* 其他发行版有自己的管理器，比如 Arch Linux 用 pacman 等。

**示例（Ubuntu 下）：**
    # 更新软件包列表索引（建议安装/升级前运行）
    $ sudo apt update

    # 安装 Git 和 Vim 编辑器
    $ sudo apt install -y git vim

    # 查看 git 的版本验证安装成功
    $ git --version
    git version 2.34.1

    # 卸载 Vim 编辑器
    $ sudo apt remove -y vim

    # 清理无用的依赖包
    $ sudo apt autoremove -y

在上例中，我们使用了 `-y` 参数，让 apt 不经交互询问直接执行（自动回答 "yes"），这在脚本安装时很常用。通过包管理器安装的软件会被记录，可以随时卸载或升级，这比从源码编译安装要方便管理。

**练习：** 使用包管理器安装一个你感兴趣的软件（例如 `tree` 用于树形显示目录结构，或 `htop` 交互式进程管理器），然后运行它测试功能；接着将其卸载，观察系统反馈的变化。

此外，Linux 系统自身的更新（包括内核、安全补丁等）也通过包管理器完成。养成定期更新系统的习惯很重要，但生产环境更新需谨慎，通常先在测试环境验证，以防兼容性问题。

### 1.6 进程与服务管理

**进程 (Process)** 是正在运行的程序实例，每启动一个程序就会产生一个进程。Linux 提供了多种查看和管理进程的工具：

* `ps`：静态地显示当前进程列表。常用 `ps -ef`（列出系统中所有进程，附带详细信息）或 `ps aux`（另一种风格的详细列表）。

* `top`：动态监控进程的工具，实时刷新显示 CPU、内存占用等，可按键交互排序。`htop` 是 `top` 的增强版（需安装）提供更好的界面。

* `pgrep`：根据进程名查询进程的 PID（进程ID）。

* `kill`：向进程发送信号以终止或控制进程。常用 `kill PID`（发送TERM信号请求进程结束），`kill -9 PID`（发送SIGKILL强制杀死进程），`kill -15 PID`（等同默认TERM）。`killall 进程名` 可以按名字终止所有匹配的进程。

* `&` 和 `CTRL+Z/fg/bg`：将进程放入后台的方法。命令末尾加 `&` 可将其放入后台执行。按 `Ctrl+Z` 可将前台进程挂起，然后用 `bg` 将其放入后台继续运行，`fg` 则可把后台进程调回前台。

**服务 (Service)** 是在后台运行的守护进程 (Daemon)，通常由操作系统在启动时或按需拉起。现代 Linux 大多使用 **systemd** 来管理系统服务。与 systemd 交互的命令是 `systemctl`：

* `systemctl status <服务名>`：查看服务状态（是否在运行、是否开机自启等）。

* `systemctl start <服务名>`：启动服务。

* `systemctl stop <服务名>`：停止服务。

* `systemctl restart <服务名>`：重启服务。

* `systemctl enable <服务名>`：设置服务开机自动启动。

* `systemctl disable <服务名>`：取消开机启动。

例如，Ubuntu 默认自带 SSH 服务 (`ssh` 或称 `sshd`)，可以用以下命令管理：
    # 查看 SSH 服务状态
    $ sudo systemctl status ssh

    # 如果没有运行则启动 SSH 服务
    $ sudo systemctl start ssh

    # 将 SSH 服务设为开机自启
    $ sudo systemctl enable ssh

    # 重启 SSH 服务以应用可能的配置更改
    $ sudo systemctl restart ssh

**示例：查看并终止进程**
    # 使用 top 查看系统资源占用最高的进程，按 q 退出
    $ top

    # 假设我们发现某进程（比如 firefox）占用了过多资源，我们可以用 pgrep 找到其 PID
    $ pgrep firefox
    4567

    # 温和地请求该进程退出
    $ kill 4567

    # 若一段时间后进程仍未退出，可以强制杀死
    $ kill -9 4567

**练习：**

* 使用 `ps -ef` 或 `ps aux` 找出系统上有哪些用户进程在运行，理解各列含义（UID、PID、启动时间、命令等）。

* 启动一个长时间运行的命令（例如 `tail -f /var/log/syslog` 持续输出日志），尝试将其挂起（Ctrl+Z）后放到后台运行（bg），再用 `jobs` 查看后台任务列表，最后用 `fg` 将其恢复前台并 Ctrl+C 终止。

* 查找并重启你的系统日志服务（通常是 `rsyslog` 或 systemd 自带 journal），然后观察相关日志文件的滚动（见下一节）。

* （进阶）编写一个死循环的小脚本运行在后台，然后练习终止它。

熟悉进程管理对于排查高负载、僵尸进程、以及确保服务正常运行很有帮助。而通过 systemctl 管理服务，是日常运维启动/停止应用、检查健康状态的基本功。

### 1.7 网络配置与调试基础

在 Linux 运维中，网络相关的命令同样重要。了解如何查看和配置网络接口、调试连通性问题，是保障服务可用的关键。

**常用网络命令：**

* `ifconfig` / `ip addr`：查看或配置网络接口的信息。`ifconfig` 是传统命令，新版本 Linux 更推荐使用功能更强大的 `ip` 命令集。`ip addr show` 显示所有接口 IP 配置；`ip route` 显示路由表。可以使用 `ip link set <iface> up/down` 来启用或禁用接口等（需管理员权限）。

* `ping`：测试网络连通性。用法：`ping <目标主机>`，它会连续发送ICMP回显请求包。如果看到回复 (reply)，则说明网络可达。Ctrl+C 可停止 ping。示例：`ping 8.8.8.8` 测试能否连接到 Google DNS；`ping -c 4 example.com` 只 ping 4 次后停止。

* `nslookup` / `dig`：DNS 查询工具。`nslookup <域名>` 可以解析域名对应的 IP；`dig <域名>` 提供更详细的 DNS 查询结果。用于检查域名解析是否正常。

* `curl` / `wget`：HTTP 请求工具。`curl` 可以用来向 URL 发送请求并获取响应头或内容，例如 `curl http://example.com` 拉取网页 HTML。也可用于测试 API 接口。`wget` 类似，但主要用于下载文件。两个工具在没有浏览器的服务器环境下非常有用。

* `netstat` / `ss`：查看网络连接和端口监听情况。`netstat -tulnp` 会列出系统当前监听的 TCP/UDP 端口及对应的进程 (需要 sudo)；`ss -tulw` 提供类似功能而且更快。想知道某服务有没有在监听预期的端口，用这命令很方便 ([Devops and Linux Tutorial | GeeksforGeeks](https://www.geeksforgeeks.org/devops-and-linux-tutorial/#:~:text=Before%20starting%20with%20DevOps%2C%20learning,changes%20and%20manage%20version%20control))。

* `telnet` / `nc` (netcat)：测试 TCP 端口连通性。`telnet <IP> <port>` 尝试建立 TCP 连接，如能连接说明对方主机该端口可访问。`nc -vz <IP> <port>` 也可用于端口探测（`-z` 表示扫描模式，`-v` 详Verbose）。常用于排查某服务的端口是否被防火墙挡住或服务未监听。

* `iptables`：Linux 内置防火墙（Netfilter）的命令行接口。运维中查看或临时添加防火墙规则有时需要用到，如 `iptables -L` 列出当前规则。现代系统也可能使用 `firewalld` 或基于 nftables，但理解 iptables 的基础规则依然有意义。不过初学者可以暂时把它视为高级主题，遇到具体场景再深入学习。

**示例：网络工具的使用**
    # 使用 ip 命令查看本机网络接口和IP地址
    $ ip addr show
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
        inet 127.0.0.1/8 scope host lo
        ...
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
        inet 192.168.0.10/24 brd 192.168.0.255 scope global eth0
        ...

    # 测试与本机网关的连通性（假设网关IP为192.168.0.1）
    $ ping -c 4 192.168.0.1
    PING 192.168.0.1 ... 64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.512 ms
    ...

    # 解析域名
    $ nslookup example.com
    Server:        8.8.8.8
    Address:    8.8.8.8#53

    Non-authoritative answer:
    Name:    example.com
    Address: 93.184.216.34

    # 检查某服务端口 (比如 Web 服务 80端口) 是否在本机监听
    $ sudo ss -tulnp | grep :80

    # 请求一个网页头部信息 (-I 仅获取HTTP头部)
    $ curl -I http://example.com
    HTTP/1.1 200 OK
    Content-Type: text/html; charset=utf-8
    Content-Length: 1256
    ...

    # 测试连接外部主机的 22 端口 (SSH)
    $ nc -vz github.com 22
    Connection to github.com 22 port [tcp/ssh] succeeded!

通过这些命令，我们能够获取网络状态信息，验证DNS是否正常解析、服务器是否对外开放了某端口、网络通不通等。在排查“无法连接服务器”这类问题时，常需要多工具配合：例如先 `ping` 测试基本连通，再 `curl`/`telnet` 具体端口，逐步定位问题。

**练习：**

* 用 `ping` 测试本机环回地址 `127.0.0.1`（应始终通），测试本地局域网另一设备IP（例如路由器），测试一个互联网地址，观察延迟、TTL等参数差异。

* 用 `curl` 访问一个 HTTPS 网站（例如 `curl -I https://www.google.com`），查看其返回的 HTTP 状态码和证书信息（可加 `-v` 看详细连接过程）。

* 尝试在本机启动一个简单的 Python HTTP服务器：进入某目录后运行 `python3 -m http.server 8080`，然后用 `ss`/`netstat` 查看 8080 端口监听情况，用浏览器或 `curl localhost:8080` 测试访问。练习停止服务器后端口关闭的情况。

* 查看当前 iptables 规则（如果有），了解默认策略和已有规则。如果你的Linux启用了 UFW（Ubuntu自带防火墙）或者 firewalld，也尝试查看其状态（如 `sudo ufw status`）。

掌握网络命令，将为后续 Docker 容器网络、Kubernetes 服务发现等内容打好基础。

### 1.8 Shell 脚本与自动化基础

Linux 的强大之处在于**脚本自动化**。Shell 脚本允许我们将一系列命令写入文件，一键执行，从而自动完成重复性任务。在运维领域，编写 Bash 脚本进行环境部署、批量任务处理是常见需求。

**基础知识：**

* 脚本文件通常以 `.sh` 作为扩展名。第1行往往是 Shebang (`#!`) 指定脚本解释器，比如常见写法 `#!/bin/bash` 表示用 Bash 来执行脚本。

* 脚本需要有可执行权限 (`chmod +x script.sh`) 才能直接运行。或者也可直接用解释器执行：`bash script.sh`。

* Shell 脚本支持变量、条件判断、循环、函数等编程构造。语法相对简洁，但注意与其他高级语言略有不同，比如赋值两边不能有空格（`x=5` 正确，`x = 5` 错误）。

**示例：** 创建一个简单的 Bash 脚本 `hello.sh`：
    #!/bin/bash
    # 这是一个示例脚本：它会读取用户输入的名字，然后问好

    echo "请输入你的名字："
    read USER_NAME   # 读取输入，存入变量 USER_NAME
    echo "你好，$USER_NAME！今天是$(date +%Y-%m-%d)。祝你有美好的一天!"

保存上述内容到 `hello.sh`，赋予执行权限并运行：
    $ chmod +x hello.sh
    $ ./hello.sh
    请输入你的名字：
    张三
    你好，张三！今天是2025-04-22。祝你有美好的一天!

脚本说明：`read USER_NAME` 等待用户从终端输入，将值赋给变量 `USER_NAME`。`$USER_NAME` 用来引用变量值。`$(date +%Y-%m-%d)` 在命令中嵌入了 `date` 命令的输出（这里格式化为YYYY-MM-DD日期）。通过脚本，我们实现了与用户的交互及自动生成问候语。

**再看一个运维小脚本示例：** 假设我们要批量创建一些日志备份目录，可以编写：
    #!/bin/bash
    # 批量创建以日期命名的日志目录

    BASE_DIR="/var/log/myapp"
    DATE=$(date +%Y%m%d)
    for server in server1 server2 server3; do
        dir="$BASE_DIR/${server}_$DATE"
        mkdir -p "$dir"
        echo "Created directory: $dir"
    done

这个脚本用到了**变量**（`BASE_DIR`, `DATE`）、**命令替换**（将 `date` 输出赋值）、**循环**（`for` 遍历服务器列表）等语法。在执行后，会创建 `/var/log/myapp/server1_20250422` 等目录并输出提示。

**Shell 强大的另一个体现是管道 (|) 和重定向：** 可以将一个命令的输出通过管道传给下一个命令处理。比如：

* `grep`：在文本中搜索匹配某模式的行。例如 `ls -l /etc | grep ".conf"` 将 `/etc` 目录的长列表输出通过管道传给 grep，只保留包含“.conf”的行（查找配置文件）。

* `sort`：对文本行排序；`uniq`：去除重复行（常与 `sort` 配合，用于计算唯一值）。

* `head` / `tail`：显示文件开头或结尾的若干行。常用 `tail -f <文件>` 动态持续输出新增的行，用于实时查看日志。

* 输出重定向：`>` 将输出写入文件（覆盖），`>>` 追加输出到文件末尾。例如 `ps aux > processes.txt` 将进程列表保存到文件。

**练习：**

* 编写一个脚本，询问用户要创建几个空文件以及文件名前缀，然后自动创建这些文件（提示：使用 `seq` 命令生成数字序列，用循环创建文件）。

* 编写一个脚本，检查系统上某个服务是否运行（例如用 `pgrep` 检查进程是否存在），如果不在运行则尝试启动它，并将这些信息记录到日志文件。

* 使用管道和重定向，将 `ifconfig`（或 `ip addr`）输出通过 `grep` 提取包含 "inet" 的行，再通过 `awk` 或 `cut` 提取 IP 地址部分，将结果输出到一个文本文件中。这练习可以让你熟悉管道串联命令处理的强大。

通过练习脚本编写，零基础用户应逐步掌握 Bash 变量、流程控制以及管道重定向。虽然后续章节会接触更高级的脚本语言（如 Python）和自动化工具，但 Bash 在运维中无处不在，值得熟练掌握。

### 1.9 系统日志与故障排查

当系统出现问题时，日志文件是排查问题的第一资源。Linux 系统及服务会将重要的事件和错误记录到日志中。了解日志存放位置和查看方法，对于运维至关重要。

**日志存放：** 大多数日志位于 `/var/log` 目录下，例如：

* `/var/log/syslog` 或 `/var/log/messages`：系统通用日志，包含系统启动信息、驱动消息以及各种守护进程日志。Debian/Ubuntu 系统用 `syslog` 文件，RHEL/CentOS 则常用 `messages` 文件。

* `/var/log/auth.log`：认证和授权相关日志（如 SSH 登录失败、`sudo` 提权记录等）。

* `/var/log/kern.log`：内核日志。

* 各应用和服务也通常有自己日志文件或子目录，例如 Apache/Nginx 的访问日志 `/var/log/nginx/access.log`，MySQL 日志 `/var/log/mysql/` 等等。

现代发行版多使用 systemd，自带**journald**日志系统，将日志保存在二进制日誌中。可以通过 `journalctl` 命令查看。例如：

* `journalctl -xe`：查看最近的系统日志（包括错误级别突出显示），常用于刚发生错误后的诊断。

* `journalctl -u nginx`：查看某服务(unit)相关日志，如 nginx 服务的启动、错误日志等（前提服务使用 systemd 管理）。

* `journalctl -b`: 查看本次启动（since boot）以来的所有日志。

* 也可配合时间过滤：如 `journalctl --since "2025-04-22 08:00:00"` 查看指定时间之后的日志。

**示例：**
    # 查看最近的系统日志（可能包含服务启动失败的原因等）
    $ sudo journalctl -xe

    # 查看 ssh 服务相关的日志，比如验证登录信息
    $ sudo journalctl -u ssh

    # 如果不用 journalctl，也可以直接观察 /var/log 下的文件
    $ sudo tail -n 20 /var/log/syslog   # 查看最近20行系统日志
    $ sudo tail -f /var/log/auth.log    # 持续跟踪输出认证日志（CTRL+C 停止）

**故障排查思路：** 当遇到系统或应用故障，可遵循如下步骤：

1. **明确问题症状**：现象是什么？报错信息？哪些服务不可用？影响范围？

2. **查相关日志**：根据问题去找对应组件的日志。例如 Web 服务无法访问，就查 Web 服务器的错误日志；登录不了系统，就查认证日志；程序崩溃就查 syslog 或应用自身日志。

3. **获取错误细节**：在日志中定位错误信息或异常行为的记录。有时需要根据时间吻合度锁定日志片段。将错误信息拿去搜索（搜索引擎或社区论坛）往往能找到线索 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=,API%E6%9D%A5%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%9E%E4%BE%8B%EF%BC%8C%E5%88%9B%E5%BB%BA%E8%BF%87%E7%A8%8B%E4%B8%AD%E5%8C%85%E6%8B%AC%E5%88%A9%E7%94%A8Nova%E6%9C%8D%E5%8A%A1%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%9E%E4%BE%8B%EF%BC%8C%E8%99%9A%E6%8B%9F%20%E6%9C%BA%E5%AE%9E%E4%BE%8B%E9%87%87%E7%94%A8Glance%E6%8F%90%E4%BE%9B%E9%95%9C%E5%83%8F%E6%9C%8D%E5%8A%A1%EF%BC%8C%E7%84%B6%E5%90%8E%E4%BD%BF%E7%94%A8Neutron%E4%B8%BA%E6%96%B0%E5%BB%BA%E7%9A%84%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%88%86%E9%85%8DIP%E5%9C%B0%E5%9D%80%EF%BC%8C%E5%B9%B6%E5%B0%86%E5%85%B6%E7%BA%B3%E5%85%A5%E8%99%9A%E6%8B%9F%E7%BD%91%E7%BB%9C%E4%B8%AD%EF%BC%8C%E4%B9%8B%E5%90%8E%E5%86%8D%E9%80%9A%E8%BF%87Cinder%E5%88%9B%E5%BB%BA%E7%9A%84%E5%8D%B7%E4%B8%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%8C%82%E8%BD%BD%E5%AD%98%E5%82%A8%E5%9D%97%EF%BC%8C%E6%95%B4%20%E4%B8%AA%E8%BF%87%E7%A8%8B%E9%83%BD%E5%9C%A8Ceilometer%E6%A8%A1%E5%9D%97%E8%B5%84%E6%BA%90%E7%9A%84%E7%9B%91%E6%8E%A7%E4%B8%8B%EF%BC%8CCinder%E4%BA%A7%E7%94%9F%E7%9A%84%E5%8D%B7%EF%BC%88Volume%EF%BC%89%E5%92%8CGlance%E6%8F%90%E4%BE%9B%E7%9A%84%E9%95%9C%E5%83%8F%EF%BC%88Image%EF%BC%89%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87Swift%E7%9A%84%E5%AF%B9%E8%B1%A1%E5%AD%98%E5%82%A8%E8%BF%9B%E8%A1%8C%E4%BF%9D%E5%AD%98%E3%80%82))。

4. **检查最近改动**：回想系统近期做过什么更改（安装软件、修改配置、更新等），这些改动往往和故障相关。检查配置文件的正确性（语法错误等常导致服务无法启动），检查磁盘空间是否耗尽（`df -h`），内存是否不足等系统状态也是必要的。

5. **实验与验证**：尝试恢复默认配置、重启相关服务，看问题是否解决。使用分步骤二分法定位问题：逐个排除可能原因。

6. **长期方案**：临时解决后，还应寻找根本原因并采取措施防止再次发生。例如如果是配置导致的，就完善文档和配置审核；如果是资源不足导致，就考虑扩容或优化。

**案例：服务无法启动**  
假设我们部署了 Nginx，但 `systemctl start nginx` 失败。排查步骤：

* 运行 `sudo systemctl status nginx`，看到状态报告“failed”。

* 执行 `sudo journalctl -u nginx`，查看日志。例如日志显示：“nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)”。这表明80端口已被占用。

* 使用 `sudo ss -tulnp | grep :80` 找到占用80端口的进程（可能是另一个Web服务）。

* 决策：要么停止冲突的服务，要么修改 Nginx 配置监听别的端口。

* 修改配置 `/etc/nginx/sites-enabled/default` 将监听端口改为 8080，保存配置。

* 测试配置语法：`sudo nginx -t`，显示 OK 后重启服务：`sudo systemctl restart nginx`，成功启动。

* 再次访问验证服务正常运行。

通过上述流程，我们从日志中发现了错误原因（端口冲突），并调整配置解决了问题。

**练习：**

* 人为制造一个错误场景：比如编辑 `/etc/ssh/sshd_config` 文件，在其中加入一行错误的配置（如拼写错误的指令），然后尝试重启 SSH 服务 (`sudo systemctl restart ssh`)，预期会失败。然后查看 `sudo systemctl status ssh` 和 `sudo journalctl -u ssh`，找出报错信息，纠正配置错误，再重启服务验证恢复。

* 查看系统最近的启动日志：`journalctl -b -1` 可以查看上一次系统启动的日志。尝试找出上次关机时系统是否有报错信息（如某服务停止超时等）。

* 检查 cron 定时任务日志：cron任务失败也会记录日志。在 Ubuntu，可以在 `/var/log/syslog` 中筛选 cron 相关行；在 CentOS，有 `/var/log/cron` 文件。尝试添加一个简单 cronjob，然后在日志中验证它的执行记录。

通过对日志的充分利用，运维工程师可以在复杂系统中抽丝剥茧，找出问题症结所在。**“让数据说话”** 是排障的金科玉律，而日志就是最重要的数据来源之一。

* * *

完成本章学习后，读者应当对 Linux 系统有了扎实的基础：能够在命令行下自如地执行文件管理、用户权限配置，安装软件、监控进程和服务运行状态，编写基本脚本以提升工作效率，并通过日志和系统工具进行故障诊断。这些技能是继续学习 Docker、Kubernetes 等云原生技术的根基。请确保多加练习，每一部分内容都可以通过亲自动手操作来加深理解。
第二部分：Docker 容器化技术
-----------------

在熟悉 Linux 基础之后，接下来进入云原生技术栈的重要组成部分：**容器化（Containerization）**。Docker 是当前流行的容器引擎，它让应用打包部署变得轻量、高效和一致。通过 Docker，我们可以将应用程序及其依赖封装在标准化的容器镜像中，在任何环境下确保运行一致，从而“**一次构建，到处运行**”。

本章将从容器的概念讲起，然后介绍 Docker 的安装使用、常用命令、镜像构建、数据管理、网络配置以及多容器编排 (Docker Compose) 等内容，并提供大量示例帮助读者掌握 Docker 的核心功能。

### 2.1 容器与虚拟机概念区别

**什么是容器？** 简单说，容器是操作系统层级的虚拟化技术，它与传统虚拟机 (VM) 的最大区别在于：**容器在主机共享同一个操作系统内核，只隔离应用及其运行环境**，而虚拟机则模拟一整套硬件并运行完整操作系统 ([Containers vs Virtual Machines | Atlassian](https://www.atlassian.com/microservices/cloud-computing/containers-vs-vms#:~:text=Containers%20vs%20Virtual%20Machines%20,hardware%20layers%20and%20containers)) ([容器与虚拟机：有何区别](https://www.redhat.com/zh/topics/containers/containers-vs-vms#:~:text=%E5%AE%B9%E5%99%A8%20%E5%92%8C%20133%E6%98%AF%E5%B0%81%E8%A3%85%E8%AE%A1%E7%AE%97%E7%8E%AF%E5%A2%83%E7%9A%84%E4%B8%A4%E7%A7%8D%E6%96%B9%E5%BC%8F%EF%BC%8C%E5%85%B6%E4%B8%AD%E6%95%B4%E5%90%88%E4%BA%86%E5%90%84%E7%A7%8D%20IT%20%E7%BB%84%E4%BB%B6%E5%B9%B6%E5%B0%86%E5%85%B6%E4%B8%8E%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%85%B6%E4%BB%96%E9%83%A8%E5%88%86%E9%9A%94%E7%A6%BB%E5%BC%80%E6%9D%A5%E3%80%82%E4%BA%8C%E8%80%85%E4%B9%8B%E9%97%B4%E7%9A%84%E4%B8%BB%E8%A6%81%E5%8C%BA%E5%88%AB%E5%9C%A8%E4%BA%8E%E9%9A%94%E7%A6%BB%E4%BA%86%E5%93%AA%E4%BA%9B%E7%BB%84%E4%BB%B6%EF%BC%8C%E8%BF%99%E5%8F%8D%E8%BF%87%E6%9D%A5%E5%8F%88%E5%BD%B1%E5%93%8D%E4%BA%86%E6%AF%8F%E7%A7%8D%E6%96%B9%E5%BC%8F%E7%9A%84%E8%A7%84%E6%A8%A1%E5%92%8C%E5%8F%AF%E7%A7%BB%E6%A4%8D%E6%80%A7%E3%80%82))。这种差异使容器更加轻量、启动速度快、资源开销小。

用一个类比来解释：如果将虚拟机比作「整栋房子」——每个VM都有自己的操作系统就像每栋房子自带完整的水电暖设施；那么容器就是同一栋大楼内的「各个公寓」——所有容器共享主楼的基础设施（操作系统内核），但彼此隔离，应有尽有各自的应用环境。共享内核意味着容器更轻量，但隔离级别略逊于完整虚拟机 ([Containers vs. virtual machines | Microsoft Learn](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/containers-vs-vm#:~:text=The%20following%20table%20shows%20some,differences%20of%20these%20complementary%20technologies))。

容器技术的兴起源自 Linux 内核提供的**cgroup（控制组）**和**namespace（命名空间）**功能：cgroup负责限制容器可用的资源（CPU、内存、IO等），namespace则隔离容器的进程、网络、文件系统等环境。Docker 利用这些机制，实现了对进程的封装隔离，形成了便携的容器格式。

**Docker 与容器镜像：** Docker 包括镜像（Image）和容器（Container）两个核心概念。镜像是一个只读的**模板**，包含了运行应用所需的文件系统和依赖配置（例如，一个Ubuntu + Nginx的镜像，内含Ubuntu系统和Nginx软件的安装）；容器则是镜像的**运行实例**，类似于面向镜像模板启动的一个进程。可以把镜像比作类，容器比作根据类创建的对象。

Docker 镜像可以通过分层技术高效复用和快速分发。镜像层叠加组成最终文件系统，每层只记录变化部分，这让镜像既易于维护又便于共享（常见的官方基础镜像如 ubuntu、alpine 等可被拉取复用）。当运行容器时，Docker 会在镜像的只读层上方添加一个可写层（写时复制），容器内对文件的修改都会写到这一层，实现环境隔离。

**容器的优势：**

* **轻量快速：** 因为无需启动完整操作系统内核，容器的启动通常在秒级甚至毫秒级，相比启动VM（通常要几十秒以上）快得多。 ([Containers vs VMs](https://www.redhat.com/en/topics/containers/containers-vs-vms#:~:text=functionalities%20needed%20for%20an%20application,way%20of%20handling%20process%20isolation))

* **一致性和可移植：** 应用在容器内的运行环境不受外部OS影响，开发环境和线上环境只要镜像相同，行为就一致。“Works on my machine”的问题迎刃而解。

* **高密度部署：** 在一台主机上可以运行数量众多的容器而不出现像开许多VM那样的高开销，更有效利用硬件资源。

* **DevOps 友好：** 容器天然适合 CI/CD 流水线，可以轻松地构建镜像发布，滚动更新应用，同时具备回滚能力（镜像是不可变的版本化artifact）。

当然，容器也有一些挑战和限制，比如对图形界面应用支持不佳、需要重新思考持久化存储方式、以及隔离不及虚拟机强（容器逃逸问题需要通过加强内核安全和用户权限控制来防范）。总体而言，容器非常适合云原生微服务架构下的应用交付，也是 Kubernetes 等编排系统的基础单位。

### 2.2 Docker 安装与快速入门

**Docker 的架构：** Docker 采用客户端-服务端架构。Docker 引擎包含一个守护进程（`dockerd`）作为服务端，负责管理镜像和容器；以及一个客户端命令行工具（`docker`），用户通过 CLI 向守护进程发送请求。默认情况下，Docker 客户端通过本地主机的 UNIX socket 与 Docker 守护进程通信。Docker 将镜像存储在本地主机或远程镜像仓库（如 Docker Hub）中。

**安装 Docker：** Docker 分为社区版 (Docker CE) 和企业版，这里使用免费开源的社区版即可。具体安装方法视操作系统而定：

* **在 Ubuntu/Debian 上：** 可以使用 APT 包管理器。首先安装依赖 `apt-transport-https ca-certificates curl gnupg`，然后添加 Docker 官方 GPG 密钥和稳定版仓库，执行 `sudo apt update` 后安装 `docker-ce` 等包（详细步骤可参考 Docker 官方文档）。简化方法：Ubuntu 可以直接 `sudo apt install docker.io`，这会安装系统源中的 Docker 版本。

* **在 CentOS 上：** 使用 `yum` 安装 `yum-utils` 然后添加 Docker 仓库，再 `yum install docker-ce docker-ce-cli containerd.io`。

* **对于 Windows/Mac 用户：** 可以安装 Docker Desktop，它在 Windows/macOS 上提供了 Docker 引擎的轻量 VM 环境以及图形化管理界面。

安装完成后，启动 Docker 服务：`sudo systemctl start docker`（Linux 上）并设置开机启动 `sudo systemctl enable docker`。可以通过 `docker --version` 验证安装成功。**（注意**：Linux 上执行 docker 命令通常需要 root 权限。可以通过将用户加入 `docker` 组来免sudo运行，如 `sudo usermod -aG docker yourname` 后重新登录生效。）

**hello world：** Docker 官方提供了一个测试镜像 `hello-world`。第一次运行它是一个很好的功能验证：
    $ docker run hello-world

如果 Docker 正常工作，会看到 Docker 从网上拉取 `hello-world` 镜像，启动一个容器运行其中的程序，输出一段欢迎和自检信息，然后容器退出。输出内容类似于：
    Hello from Docker!
    This message shows that your installation appears to be working correctly.
    ...

这说明 Docker 引擎已经成功地下载镜像并运行了容器。

### 2.3 Docker 常用命令与操作

Docker 提供了丰富的命令行工具来管理镜像和容器。下面介绍最常用的几类命令：

**镜像管理相关：**

* `docker pull <镜像名>:<标签>`：从远程仓库拉取镜像。如果不指定标签，默认为 `latest`。例如 `docker pull ubuntu:20.04`。

* `docker images`：列出本地已有的镜像。会显示仓库名、标签、镜像ID、大小等信息。

* `docker rmi <镜像ID或名称>`：删除本地镜像。加 `-f` 可强制删除（当有容器在使用该镜像时需要强制才行）。

* `docker search <关键词>`：搜索Docker Hub上的公共镜像。

**容器生命周期相关：**

* `docker run`：运行容器的主要命令。常用参数：
  
  * `--name <容器名>`：为容器指定一个名称，方便后续管理，否则会自动生成随机名字。
  
  * `-d`：后台运行容器（detached 模式），这样命令不会阻塞终端。
  
  * `-it`：通常连用，`-i` 保持标准输入打开（交互模式），`-t` 分配一个伪TTY。这样可以进入容器交互。
  
  * `-p <宿主端口>:<容器端口>`：端口映射，将容器内部端口映射到主机端口上，以便外部访问容器服务。例如 `-p 8080:80` 将容器内部80端口映射到宿主机8080。
  
  * `-v <宿主目录>:<容器目录>`：挂载卷，把宿主文件夹挂载进容器，实现数据持久或共享（详细见后续存储部分）。
  
  * `--env <变量>=<值>`：设置环境变量，或者使用 `--env-file` 文件批量导入环境变量。
  
  * `--restart <策略>`：设置容器退出后的重启策略，如 `--restart unless-stopped` 表示除非手动停止，否则异常退出后自动重启。用法示例：

      docker run --name webserver -d -p 8080:80 nginx:latest

  这将后台运行一个 Nginx 容器，将容器80端口映射到宿主8080。可以通过浏览器访问 [http://localhost:8080](http://localhost:8080/) 验证。

* `docker ps`：列出当前运行的容器。加 `-a` 则包括所有容器（包括已停止的）。

* `docker stop <容器名或ID>`：停止容器（给容器内进程发送 SIGTERM 信号，超时后 SIGKILL）。

* `docker start <容器名或ID>`：启动一个已停止的容器（它会保留之前的状态，继续运行）。

* `docker restart <容器名或ID>`：重启容器。

* `docker rm <容器名或ID>`：删除容器（容器必须先停止，才能删除）。加 `-f` 可以强制删除正在运行的容器（会先杀掉再删除）。

* `docker logs <容器名>`：查看容器日志输出，加 `-f` 可以跟随日志动态输出，加 `--tail n` 只看最后n行。

* `docker exec -it <容器名> /bin/bash`：在一个正在运行的容器内执行命令。常用于打开一个交互shell，以调试容器内部环境（需容器镜像里有 /bin/bash）。例如上面的 Nginx 容器，可以用 `docker exec -it webserver /bin/bash` 进入，查看配置或日志，然后 `exit` 退出。

* `docker inspect <容器名>`：查看容器的详细配置和状态（JSON 格式输出），包括网络IP、挂载卷信息等。

**示例：交互式运行 Ubuntu 容器**
    # 拉取最新的 ubuntu 基础镜像
    $ docker pull ubuntu:latest

    # 以交互模式运行一个 ubuntu 容器，在容器内打开 bash shell
    $ docker run -it --name myubuntu ubuntu:latest /bin/bash

    root@5c6f9ccb4c08:/# echo "Hello from inside container"
    Hello from inside container
    root@5c6f9ccb4c08:/# cat /etc/os-release | grep PRETTY_NAME
    PRETTY_NAME="Ubuntu 22.04.2 LTS"
    root@5c6f9ccb4c08:/# exit   # 输入 exit 退出容器的shell

退出后该容器将停止，但还存在（状态为 Exited，可用 `docker ps -a` 查看）。可以通过 `docker start -ai myubuntu` 再次进入（`-a`附加终端，`-i`交互）。

**示例：查看日志和移除容器**
    # 查看先前启动的 webserver 容器日志最后5行
    $ docker logs --tail 5 webserver

    # 停止并移除 webserver 容器
    $ docker stop webserver
    $ docker rm webserver

    # 一条命令强制删除一个运行中的容器（谨慎使用）
    $ docker rm -f myubuntu

**练习：**

* 使用 `docker run` 启动一个官方的 **Redis** 数据库容器（镜像为 `redis`）。不需要参数即可前台运行（因为 Redis 默认就是前台打印日志）。在另一个终端，用 `docker ps` 查看它的状态，然后用 `docker logs` 读取 Redis 启动日志。最后停止并删除该容器。

* 拉取 `nginx` 镜像并运行两个容器实例，一个映射80端口到宿主8081，另一个映射到8082（用 `--name` 区分容器名称）。然后分别访问这两个端口确认都能返回 Nginx 的欢迎页。思考：两者都是基于同一镜像运行的，相互之间是否有影响？如果修改其中一个容器内的文件，对另一个有无影响？（提示：容器之间相互隔离，每个都有各自的可写层）

* 启动一个容器并使其每隔1秒输出一条信息（可以用 `bash -c "while true; do echo hello; sleep 1; done"` 作为容器命令）。让它后台运行，然后练习使用 `docker logs -f` 实时查看输出，再用 `docker stop` 停止它。结合 `docker ps -a` 观察容器状态变化。

掌握上述基本操作命令后，就能熟练地启动、停止容器，查看其状态和日志。接下来我们将深入 Docker 的核心：构建自己的镜像，以及更高级的容器数据管理和网络配置。

### 2.4 编写 Dockerfile 和构建镜像

Docker 的魅力在于**自定义镜像**。我们可以通过编写 **Dockerfile**（文本文件，包含一系列指令）来定义镜像内容，使用 `docker build` 将其构建出来。Dockerfile 类似于一份配方，定义了基于哪个基础镜像、拷贝哪些文件、执行哪些命令来安装依赖、设置环境变量和启动命令等。

**Dockerfile 基本指令：**

* `FROM <基础镜像>`：指定基础镜像，所有镜像必须以某个基础为起点（可以是官方的如 `ubuntu:20.04`，也可以是自定义的镜像）。FROM 通常是第一条指令。

* `MAINTAINER`：定义维护者信息（现在已被 LABEL 替代，用 LABEL 定义元数据更灵活）。

* `LABEL`：设置镜像元数据标签，如作者、版本等。

* `RUN <命令>`：在构建镜像时执行的命令。这些命令会在镜像构建时运行其结果被提交到镜像的新层。例如 `RUN apt update && apt install -y python3`。

* `COPY` 或 `ADD`：将主机上的文件添加进镜像文件系统。例如 `COPY src/ /app/src/` 把当前构建上下文下的src目录复制到镜像内的 /app/src。

* `WORKDIR <路径>`：设置工作目录，后续命令的相对路径都基于此目录，相当于 `cd`。并且容器启动时默认也在该目录下。

* `ENV <变量> <值>`：设置环境变量，会在运行容器时存在。

* `EXPOSE <端口>`：声明容器运行时监听的端口（仅文档效果，方便他人了解，不会自动发布端口）。

* `CMD <命令>`：指定容器启动时要执行的命令（容器的默认入口指令）。Dockerfile 里只能有一个 CMD，如果定义多个则只有最后一个生效。CMD 可以在 `docker run` 时被用户指定的命令覆盖。

* `ENTRYPOINT <命令>`：入口点指令，与 CMD 配合使用，当想固定容器的执行命令而不被覆盖时使用 ENTRYPOINT，把可变部分作为 CMD 参数。例如 ENTRYPOINT ["python", "app.py"]。一般简单情况下用 CMD 就够了。

**构建镜像：** 准备好 Dockerfile 后，使用 `docker build` 命令。在包含 Dockerfile 的目录下执行：  
`docker build -t <镜像名:标签> <Dockerfile所在路径>`  
如 `docker build -t myapp:1.0 .` （注意末尾的 `.` 表示上下文路径为当前目录）。构建过程会按 Dockerfile 指令顺序执行。每条指令构成镜像的一层，如果中间某步没有变化，下次构建会利用缓存加速。

**示例：编写一个简单镜像**  
假设我们想制作一个自定义镜像，该镜像基于 Alpine Linux（一个轻量发行版），包含一个问候脚本，每次容器启动时打印问候语。

首先，在一个空目录创建文件 `greet.sh`，内容如下：
    #!/bin/sh
    echo "Hello, this is a custom container. The date is $(date)."

然后编写 Dockerfile：
    # 使用 Alpine 作为基础镜像
    FROM alpine:3.17

    # 将问候脚本复制进镜像的 /app 目录
    COPY greet.sh /app/greet.sh

    # 设置脚本可执行权限
    RUN chmod +x /app/greet.sh

    # 声明默认工作目录
    WORKDIR /app

    # 指定容器启动执行脚本
    CMD ["./greet.sh"]

文件准备好后，在该目录执行构建：
    $ docker build -t greeting:latest .

构建成功后，本地就有了一个名为 greeting 的镜像。现在运行容器测试：
    $ docker run greeting:latest
    Hello, this is a custom container. The date is Tue Apr 22 09:45:00 UTC 2025.

可以看到容器启动后执行了我们的脚本并退出。

如果希望容器启动后不立即退出，可以将脚本改为长期运行的服务或进入休眠等待。例如加入 `tail -f /dev/null`（一直挂起等待）到 CMD，让容器保持运行。但在此例中我们只是演示输出信息然后结束。

**再示例：构建一个简单Web应用镜像**  
以下Dockerfile基于 Python 镜像运行一个 Flask web应用：
    FROM python:3.9-slim

    WORKDIR /app

    # 将当前目录代码复制进镜像
    COPY . .

    # 安装依赖
    RUN pip install --no-cache-dir -r requirements.txt

    # 暴露服务端口
    EXPOSE 5000

    # 指定容器启动命令
    CMD ["python", "app.py"]

这个Dockerfile假定当前目录有 `app.py` 和 `requirements.txt`。构建后，会产生一个镜像，在运行容器时自启动 Python 应用监听5000端口。

**镜像优化：** 构建镜像时需要注意减小体积和提高层缓存利用。例如：

* 尽量选择小的基础镜像（如 Alpine、slim 版基础镜像）。

* 合理地合并 RUN 指令，减少层数。例如 apt 安装前后用 && 合并成一层，并清理缓存：
  
      RUN apt update && apt install -y <packages> && rm -rf /var/lib/apt/lists/*

* 不要在镜像中包含无关文件，使用 `.dockerignore` 文件排除构建上下文中不需要的内容（类似 .gitignore）。

* 对于非常大的运行时，可以考虑多阶段构建（multi-stage），先编译构建在第一个阶段镜像，然后仅将所需的编译产物复制到更小基础的第二阶段镜像中，从而减小最终镜像体积。

**练习：**

* 编写 Dockerfile，将一个简单静态网站（几个 HTML 文件）打包为镜像并用 Nginx 服务来托管。在 Dockerfile 中，FROM `nginx:alpine` 作为基础，COPY 静态文件到 `/usr/share/nginx/html`，这样运行容器即提供静态网站服务。

* 编写 Dockerfile 制作自己的 Ubuntu 定制环境，比如安装一些常用工具（如 curl、vim），设置时区或环境变量，然后构建镜像并运行个容器验证工具是否都在。

* 尝试在 Docker Hub 上查找 `Dockerfile` 的最佳实践指南，修改优化你的 Dockerfile，例如减少层、利用缓存等。对比优化前后的镜像大小（用 `docker images` 查看）和构建速度。

通过编写 Dockerfile 并构建运行自定义镜像，读者将深入理解 Docker 镜像和容器的工作原理，以及如何将应用封装其中。这为后续学习 Kubernetes 部署云原生应用打下良好的基础。

### 2.5 数据卷与持久化存储

在默认情况下，容器中产生的数据（写入文件的更改）存储于容器的可写层。当容器删除后，这些数据也会随之销毁。这对于**无状态应用**不是问题（例如 web 前端容器，不需要持久保存什么数据），但对于**有状态应用**（如数据库）而言，就需要将数据持久化。Docker 提供了 **数据卷 (Volume)** 和 **绑定挂载 (Bind Mount)** 两种方式，来实现容器与宿主之间的数据持久。

**数据卷 (Volume)：** 由 Docker 管理的宿主机目录，可以挂载到容器内部。它独立于容器的生命周期，容器删除了卷中的数据仍保留。卷可以被多个容器挂载，共享数据。Docker 提供命令来管理卷：

* 创建卷：`docker volume create mydata`

* 列出卷：`docker volume ls`

* 查看卷详细信息：`docker volume inspect mydata`

* 删除卷：`docker volume rm mydata`（需确保没有容器在使用该卷）

当使用 `docker run -v 卷名:容器目录` 时，如果卷不存在Docker会自动创建。例如：`docker run -d -v mydata:/var/lib/mysql mysql`，Docker会将名为 "mydata" 的卷挂载到容器的 /var/lib/mysql（MySQL 的数据目录），确保数据库文件保存在宿主。

**绑定挂载 (Bind Mount)：** 将宿主机上**指定路径**挂载到容器内。跟卷不同的是，这完全由用户管理，不通过 Docker volume 管理命令。用法也是 `-v` 参数，不过源路径直接给出宿主绝对路径。比如：  
`docker run -d -v /home/user/appdata:/app/data myimage`  
这样宿主 `/home/user/appdata` 目录就映射为容器内 `/app/data`，容器对该目录的读写都会反映到宿主机上。Bind mount 的好处是简单直接，可以让容器使用宿主现有文件（常用于开发调试，把源码挂载进容器）。但要注意路径必须宿主真实存在，且权限能让容器内进程访问；Docker 不会隔离或管理这个路径，也不适合跨不同主机使用。

**tips:** 在 Docker for Windows/Mac 的环境下，Bind mount 时目录路径写法和权限可能有特殊要求，具体请参考对应文档。

**示例：使用 Volume 保持数据持久**
    # 创建一个数据卷
    $ docker volume create myvol

    # 运行容器挂载该卷，在容器内向卷写入数据
    $ docker run --name voltest -it -v myvol:/data busybox sh
    / # echo "12345" > /data/numbers.txt
    / # ls /data
    numbers.txt
    / # exit   # 退出容器，容器随即停止

此时容器voltest已停止甚至可以删除，但卷 myvol 里面的数据仍在。我们可以重新启动一个容器来验证：
    # 使用同一个卷启动新容器，检查文件是否存在
    $ docker run --rm -v myvol:/data busybox cat /data/numbers.txt
    12345

可以看到，我们在新容器中成功读到了之前写入卷的内容。`--rm` 参数让容器退出时自动删除（因为只是做一次读取测试）。

**示例：使用 Bind Mount 进行本地开发**

假设本地有一个目录 `/home/alice/webapp` 存放网页文件，我们希望容器里的 Nginx 能直接使用这些文件提供服务，以便改动立即生效而不用重建镜像。可以：
    $ docker run -d --name web -p 8080:80 -v /home/alice/webapp:/usr/share/nginx/html:ro nginx:latest

这里我们使用 `:ro` 将挂载设为只读（容器内无法修改宿主文件，仅提供服务）。现在访问 [http://localhost:8080](http://localhost:8080/) 就是宿主 `/home/alice/webapp` 目录下的内容。如果修改宿主文件，刷新浏览器即可看到变化，无需重新构建或复制进容器。

**注意容器内UID映射：** Bind mount 时，如果宿主目录中文件属主与容器进程用户不符，可能会遇到权限问题。例如 Nginx 容器中的进程用 www-data 用户，UID 可能为 101，而宿主 `/home/alice/webapp` 文件属主是 alice (UID 1000)，默认情况下容器内视这些文件属主为未知 UID，权限可能不足。解决方法：可以在宿主调整目录权限为全局可读，或者启动容器时用 `-u` 指定以某UID运行。但最简单的是在需要交互写入时使用 Volume 或在容器镜像中协调UID。初学者可先尽量使用卷或开放权限简化问题。

**删除容器时保留数据：** 默认情况下，如果使用 Named Volume 或 Bind Mount，删除容器不影响数据。但如果使用 Docker Desktop 或 Docker Compose 等，有选项可以自动清理卷，需小心。可以通过 `docker run --rm` 来让容器结束自动删容器但不会删挂载的数据卷。还有 docker 提供 `docker system prune` 来清理未使用的资源，执行时要注意不要误删有用的数据卷（可以带参数控制是否删卷）。

**练习：**

* 使用 `mysql` 官方镜像启动数据库容器，并使用 volume 挂载其数据目录。步骤：创建一个名为 `mysqldata` 的卷，用 `-v mysqldata:/var/lib/mysql` 运行 MySQL（记得用 `-e MYSQL_ROOT_PASSWORD=mysecret` 设置 root 密码环境变量）。执行后，用 `docker exec` 进入该容器，创建一个数据库和一张表插入一些记录。然后删除容器，重新用同样方式（挂同一个卷）启动一个新的 MySQL 容器，验证之前创建的数据仍然存在。

* 实验 Bind mount 的权限：在宿主建立一个目录，创建一个文件写入一些文字。然后运行一个容器挂载该目录，尝试读取文件。再尝试从容器内写入一个新文件，看看宿主是否出现该文件。如果权限错误导致写失败，尝试用 `:Z` (SELinux 情况下) 或调整权限为777，再测试写入成功情况。

* 查阅资料了解 docker volume 的驱动机制：Docker 默认卷存在宿主 `/var/lib/docker/volumes` 下。可以试着用 `docker volume inspect` 找到具体路径并验证文件确实存储在宿主。了解还有 NFS、tmpfs 等卷驱动可用（进阶）。

通过卷和绑定挂载，我们能够安全地处理容器数据，实现持久化和共享，这也为在 Kubernetes 中使用 PersistentVolume 打下基础概念。

### 2.6 容器网络与端口映射

Docker 默认在宿主上创建了一个名为 **docker0** 的虚拟网桥，以及一套内部网络机制，使得容器可以互相通信，并能通过NAT访问外部网络。理解 Docker 网络模式，有助于我们配置容器间通讯和对外暴露服务。

**Docker 网络驱动：** Docker 提供几种网络模式/驱动：

* **bridge（默认）：** 桥接网络。当启动Docker服务时，会创建一个docker0网桥接口，默认子网通常172.17.0.0/16。每创建一个容器，Docker会在宿主上创建一对 veth 虚拟网卡，一端加入 docker0 网桥，另一端放入容器内部作为 eth0，并分配IP。这使得**同一宿主上的容器彼此处于一个局域网**（docker0桥接的子网内），可以通过IP直接通信。同时，容器访问外网会通过 NAT 转发到宿主出口。而**外界不能直接访问容器**，除非通过端口映射或其它网络配置。

* **host：** 主机网络模式。容器不获得独立网卡，直接使用宿主网络栈。容器中服务监听的端口直接就是宿主的端口，没有 NAT。所以这种模式下 `-p` 端口映射无效，因为不需要。host 模式适合对网络性能要求高或需要和宿主上服务共用IP的场景，但容器间不隔离端口空间。

* **none：** 无网络模式。容器不会分配网络接口。这种容器完全没有联网功能，除非在运行时通过 `docker network connect` 接入某网络。多用于需要自定义网络栈或者完全隔离网络的特殊场景。

* **container：** 容器间共享网络堆栈模式。使用 `--network container:<容器名>`，新容器不会创建自己的网络namespace，而是加入已有容器的网络。这样两个容器相当于在同一个网络栈，能够通过 localhost 直接通信。典型应用是运行一些辅助容器，比如一个专门的流量抓包容器共享主应用容器网络。

* **自定义桥接网络：** 用户可以创建自定义的桥接网络：`docker network create mynet`，然后运行容器时使用 `--network mynet`。容器加入自定义网络后，会获得一个IP，而且 Docker 会在该网络内为容器设置**DNS别名**为容器名称，方便通过名称互访。这种方式常用于 Docker Compose，使同一应用栈内的容器可以通过服务名互相访问（比直接用docker0方便管理，且隔离不同应用组的网络）。

**容器互联 (legacy link)**：Docker 旧版有 `--link` 参数，可以连接两个容器并在源容器内设环境变量指向目标IP，但这已被自定义网络+DNS机制所取代。

**端口映射 (Port Mapping)：** 如前所述，在默认bridge网络模式下，容器没有直接暴露在宿主网络。为了让宿主（甚至宿主外部）访问容器服务，需要使用 `docker run -p` 参数进行端口映射。其原理是在宿主上监听指定端口，将收到的流量转发到容器的对应端口。

`-p [host_ip:]host_port:container_port` 可以指定映射，host_ip 部分可选（默认监听所有地址）。也可以用 `-p host_port:container_port/udp` 来指定 UDP 协议。支持映射多端口。**常见简写：** `-p 8080:80` 相当于 `宿主0.0.0.0的8080 → 容器内部80 (tcp)`。

**示例：多个容器在默认网络互通**
    # 启动两个容器，不映射端口，仅内部通信
    $ docker run -d --name alpine1 alpine:latest sleep 1000
    $ docker run -d --name alpine2 alpine:latest sleep 1000

    # 获取它们的IP
    $ docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' alpine1
    172.17.0.2
    $ docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' alpine2
    172.17.0.3

    # 从 alpine1 ping alpine2 （需要容器有ping命令，alpine默认没有，可以用busybox代替）
    $ docker exec alpine1 ping -c 3 172.17.0.3
    PING 172.17.0.3 ... 64 bytes from 172.17.0.3: seq=1 ttl=64 time=0.089 ms
    ...

可以看到它们处于 172.17.0.0/16 网络，可以互相通信。但用容器名则不行，因为默认网络下 Docker 不提供自动解析容器名（除非使用 `--link` 或自定义网络）。

**示例：使用自定义网络和名称解析**
    # 创建一个用户自定义桥接网络
    $ docker network create mynetwork

    # 在该网络启动两个容器，设置别名以便互相识别
    $ docker run -d --name db --network mynetwork redis:alpine   # 启一个Redis服务做模拟后端
    $ docker run -d --name app --network mynetwork alpine:latest sleep 1000

    # 从 app 容器ping 主机名为 db（Docker会解析为db容器的IP）
    $ docker exec app ping -c 3 db
    PING db (172.18.0.2): 56 data bytes
    64 bytes from 172.18.0.2: seq=0 ttl=64 time=0.127 ms

自定义网络分配的是另一个子网（例如172.18.0.0/16），并且**容器名自动成为网络内的DNS主机名**。上例 app 容器能以 "db" 名称访问到 redis 容器，非常方便。

**示例：端口映射访问**
    # 运行一个HTTP服务器容器并映射端口
    $ docker run -d --name web -p 5000:80 nginx:alpine

    # 在宿主访问 http://localhost:5000
    # (可以使用curl验证)
    $ curl -I http://localhost:5000
    HTTP/1.1 200 OK
    ...

浏览器访问宿主IP的5000端口，就能到达容器内的Nginx（80端口）。Docker在内部做了NAT转发。可以通过 `docker port web 80` 查看自动分配的宿主端口（如果用 `-P`大写，表示随机映射一个宿主端口，这命令可查询映射详情）。

**网络隔离：** 默认bridge模式下，所有容器（未指定特殊网络的）共享docker0网桥，因此**所有容器彼此可达**。有时我们希望隔离不同应用的容器，让它们网络上互相不可见，就需要用自定义网络，把不同应用放不同网络中。Docker默认不会跨网络路由，所以不同bridge网络的容器不能直接通信。必要时可以用 `docker network connect` 将某容器加入额外的网络来实现跨网络通信。

**练习：**

* 分别启动两个容器：一个运行 `httpd` (Apache) 映射宿主端口8080，另一个运行 `nginx` 映射宿主端口8081。验证两者都能通过浏览器访问。同时进入其中一个容器，尝试访问另一个容器的服务（可能需要容器安装 `curl` 或 `wget`），看是否通畅（应可以通过宿主IP:端口访问，但直接通过容器IP默认不通，因为没有在对方容器开放端口映射给这一侧容器；可尝试用自定义网络把两者放一起然后用容器IP测试）。

* 创建两个自定义网络 net1 和 net2，在 net1 上启动容器 A、B，在 net2 上启动容器 C。测试 A 能 ping B（可以），A 不能 ping C（不同网络不可达）。然后用 `docker network connect net1 C` 把 C 同时加入 net1，测试 A ping C（现在应可以通）。思考：这样C有两个网络接口，可以用 `docker inspect C` 查看。

* 了解 Docker Compose 对网络的处理：默认 Compose 会为同一应用的容器建立一个隔离网络，服务名作为DNS名。可以尝试写一个简单 docker-compose.yml 启两个容器（如 web 和 db），启动后在其中一个容器内用服务名访问另一个，验证网络联通。

通过以上练习和示例，你会对 Docker 网络模型有直观认识。在实际环境中，合理规划容器网络能提升安全性和通信效率。例如，把数据库容器和后端容器放在同一网络，前端容器另一个网络，只通过反向代理打通，而不让前端直接访问数据库所在网络。

### 2.7 Docker Compose：多容器编排

随着应用复杂度提高，常常需要**多容器**协同工作（例如 Web 前端 + 后端 + 数据库）。手动使用 `docker run` 启动多个容器，管理它们的参数和依赖会变得繁琐。**Docker Compose** 是 Docker 官方提供的工具，帮助我们用一个 YAML 文件来描述一组相关联的容器服务，一键启动或停止整个应用栈。

**Compose 基本概念：** Docker Compose 使用一个默认文件 `docker-compose.yml` 来定义应用服务。主要要素包括：

* **services：** 一组服务，每个服务对应一个镜像，可看作一个容器模板。可以在 service 下定义镜像、构建上下文、命令、端口、卷、环境变量、依赖等，与 `docker run` 参数对应。

* **networks：** 可选，自定义 Compose 应用使用的网络。如果不显式指定，Compose 会默认创建一个网络，名字通常为“目录名_default”，并将所有服务连入此网络。

* **volumes：** 可选，定义数据卷。如果服务部分使用了命名卷挂载，也可以在卷部分统一定义。

Compose 通过服务的依赖关系（`depends_on` 字段）确定启动顺序，但它**不等待**服务完全就绪（这点在涉及数据库初始化等场景要自己处理重试逻辑）。

**安装 Compose：** 最新的 Docker Desktop 已内置 Compose。Linux 上可以用 pip 安装 `docker-compose` 或安装 Docker官方二进制。使用时，在定义文件目录下运行 `docker-compose up -d` 即可启动所有服务容器。

**示例：使用 Docker Compose 启动 LEMP 堆栈**  
假设我们有一个 PHP 应用，需要 Nginx 作为前端、PHP-FPM 作为应用解释、MySQL 数据库作为存储。可以编写一个 `docker-compose.yml`：
    version: '3.8'
    services:
      web:
        image: nginx:alpine
        ports:
          - "8080:80"
        volumes:
          - ./www:/usr/share/nginx/html:ro    # 将当前目录www挂载为网站根目录（只读）
          - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro  # 自定义nginx配置
        depends_on:
          - php

      php:
        image: php:8-fpm-alpine
        volumes:
          - ./www:/var/www/html:ro   # PHP容器也挂载同样的代码目录
        depends_on:
          - db

      db:
        image: mysql:5.7
        environment:
          - MYSQL_ROOT_PASSWORD=secret
          - MYSQL_DATABASE=myapp
        volumes:
          - dbdata:/var/lib/mysql

    volumes:
      dbdata:

在这个 Compose 文件中，我们定义了3个服务：web（Nginx）、php（PHP-FPM）、db（MySQL）。它们会自动共享同一个网络（无需我们手动配置，Compose默认会创建并将services连接进去）。服务名即 DNS 名，比如 Nginx 配置里可以用 `php` 主机名访问 PHP-FPM，PHP 应用连接数据库可以用 `db` 主机名。`depends_on` 确保启动顺序：db -> php -> web，但注意 MySQL 启动后可能还在初始化，不一定立刻能接受连接，需要在PHP应用代码里考虑重试。

Compose 执行 `up` 后，等一会就可以通过浏览器访问宿主8080端口，看到由 PHP 返回并经 Nginx 服务的页面。如果需要停止，执行 `docker-compose down` 将停止并移除容器（数据卷 dbdata 因为是命名卷会保留，可以在 YAML volumes字段选择 external或者用 down -v 参数来清理）。

**Compose 长处：**

* 一条命令启动/停止所有相关服务，适合开发和测试环境一键搭建复杂应用环境。

* 通过配置文件，记录了整个应用栈的依赖，方便分享和版本控制。

* 支持扩展（`docker-compose up --scale web=3` 可以快速启动多个web实例做简单负载均衡试验）和多环境配置（Compose file 支持变量，或使用多个文件组合覆盖，用于区分开发/生产参数）。

**练习：**

* 编写一个 Compose 文件，包含一个 Python Flask web 服务和一个 Redis 缓存服务。让 Flask 服务启动时连接 Redis （可以通过环境变量传入 Redis 主机名 `redis`），实现一个简单计数器（访问次数存储在 Redis）。测试 Compose 启动应用，刷新页面计数递增，证明两个服务互联工作。

* 使用 Compose 来部署 WordPress 和 MySQL，这也是官方常见示例。验证通过 Compose 能快速拉起一个可用的博客平台。然后练习 Compose 的其他命令：如 `docker-compose logs -f` 查看组合日志，`docker-compose ps` 查看当前服务状态等。

* 如果有兴趣，尝试使用 Compose 部署一个含三四个服务的应用（比如某开源项目带有 Compose 配置），体验在无编排工具时Docker管理多容器的难度，以及Compose带来的便利。

Docker Compose 是迈向编排系统（如 Kubernetes）的桥梁概念。它让我们熟悉用声明式配置文件描述多容器应用，这与 Kubernetes 中编写 YAML 清单定义 Pod、Service 等十分类似。掌握 Compose 有助于更好地理解K8s的编排思想。

### 2.8 私有镜像仓库与镜像发布

在开发和运维过程中，我们经常需要将自己构建的镜像**分发**给他人使用，或者在多台服务器上部署。这就需要一个镜像仓库 (Registry) 来存储和分享镜像。Docker Hub 是默认的公共镜像仓库，但对于企业私有应用，通常会搭建**私有镜像仓库**或者使用云厂商的容器镜像服务。

**Docker Hub：** Docker 官方运营的公共仓库，拥有大量镜像。默认 `docker pull ubuntu` 就是从 Docker Hub 拉取。使用 Docker Hub 发布自己的镜像需要注册账号，然后：

* 用 `docker login` 登录凭据。

* 将本地镜像打标签（tag）为 `username/repo:tag` 格式。

* `docker push username/repo:tag` 推送镜像到Hub上自己的仓库。

例如，如果 Docker Hub 用户名为 `alice`，想推送前面构建的 greeting 镜像，可以：
    $ docker tag greeting:latest alice/greeting:1.0
    $ docker push alice/greeting:1.0

成功的话，在任何机器上 `docker pull alice/greeting:1.0` 就能获取并运行这个镜像。

**私有仓库软件：** Docker 官方提供一个开源项目 **Registry**，可以自行部署成私有仓库。最简单的用法是运行 `registry` 镜像：
    $ docker run -d -p 5000:5000 --name registry registry:2

这将在本地启动一个HTTP服务监听5000端口作为仓库，不带鉴权（适合内网试用）。之后可以用 `docker tag` 将镜像标记为 `localhost:5000/myimage:tag` 然后 `docker push localhost:5000/myimage:tag` 推送到这个私有库，再在其他主机通过 `docker pull` 相同地址取回（需要配置该主机的Docker引擎信任这个私库地址，可以通过在 `/etc/docker/daemon.json` 添加 `{"insecure-registries":["<hostname>:5000"]}` 然后重启Docker服务来允许不安全的HTTP仓库）。

企业使用中，更加完善的是**Harbor**（由 VMware 开源的企业级镜像仓库）等，它提供Web界面、用户权限、镜像扫描等高级功能。搭建Harbor需要一些配置，可根据官方文档安装。

**镜像版本管理：** 推送镜像前要选定合适的标签 (tag)，如按照版本号或日期。要注意 Docker Hub 对免费用户的镜像数量和拉取频率有限制，私有仓库则需要注意存储空间和清理旧镜像（Harbor等提供垃圾回收）。

**最佳实践：** 构建镜像应遵循**不可变性**原则，不要在运行容器中直接修改然后commit生成新镜像。镜像的来源应该是Dockerfile构建，这样才能通过版本控制Dockerfile来重现和追溯每个镜像版本的内容。将 Docker 镜像发布到仓库后，应有相应的变更说明（可以用 LABEL 写入镜像，也可以维护CHANGELOG），方便使用者了解更新。

**安全扫描：** 公共镜像在发布前通常也要做扫描（如Trivy等工具）检查是否有已知漏洞，重要场景下要基于安全扫描结果升级底层镜像或修补高危漏洞。Harbor、Docker Hub均提供扫描功能集成。

**练习：**

* 在自己Docker Hub账号下创建一个新仓库（可以在Docker Hub网页上操作），然后把任意一个本地镜像打标签推送上去。尝试在另一台机器（或用 `docker pull` 后再 `docker run`）运行这个镜像，验证成功。完成后可以在Hub上将该镜像仓库删除以免占据空间（或将其设为私有）。

* 尝试部署官方 Registry 镜像作为私有库。在本机推送一个镜像到 `localhost:5000`，然后从同一主机pull验证。进阶：在另一台机器上pull（涉及 insecure registry 设置）。

* （了解）阅读 Harbor 的简介或安装Harbor在测试环境运行，熟悉其UI。用Harbor创建项目、用户，测试推送镜像并用不同用户拉取受权限控制的镜像。

通过掌握镜像仓库的使用，您就能将容器镜像纳入持续交付流程：在CI流水线中自动构建镜像并推送，运维环境通过pull最新镜像来部署更新。这实现了应用分发的标准化，也是云原生理念的重要一环。

* * *

本章我们系统学习了 Docker 容器技术。从容器的原理优势到 Docker 引擎的安装使用，再到常用命令、镜像构建、数据管理、网络配置和编排工具 Compose。经过充分的练习，读者应能够：

* 独立安装配置 Docker 环境，并运行基本容器应用。

* 熟练使用 Docker 命令启动、停止容器，查看日志和终端，管理镜像和数据卷。

* 编写 Dockerfile 制作自定义镜像，并优化镜像大小。

* 理解容器网络模型，配置端口映射和自定义网络让容器互联或隔离。

* 使用 Docker Compose 定义多容器应用并一键部署，简化开发测试流程。

* 将镜像推送到公共或私有仓库，实现团队共享和发布部署。

这些技能对日后学习 Kubernetes 非常关键，因为K8s在很大程度上可以看作是对大量 Docker 容器进行统筹管理和调度的系统。有了 Docker 基础，我们将在下一章深入 Kubernetes 容器编排平台的强大功能。
第三部分：Kubernetes 容器编排
--------------------

容器让应用部署更为轻量，但在生产环境中，我们通常需要管理大量容器实例，并处理服务发现、伸缩、故障恢复等复杂需求。**Kubernetes**（常简称 _K8s_）就是目前主流的容器编排平台，它负责在一个集群中自动部署、扩展和管理容器化的应用 ([Kubernetes 文档 | Kubernetes](https://kubernetes.io/zh-cn/docs/home/#:~:text=1,8))。本章节将引导零基础读者逐步认识 Kubernetes，从架构原理到基本概念，对比前面 Docker 学到的内容，体会 Kubernetes 如何帮助我们大规模地运用容器。

### 3.1 Kubernetes 简介与架构概览

**什么是 Kubernetes？** 根据官方定义：_Kubernetes 是一个开源的容器编排引擎，用来对容器化应用进行自动化部署、扩缩和管理_ ([Kubernetes 文档 | Kubernetes](https://kubernetes.io/zh-cn/docs/home/#:~:text=1,8))。它最初由 Google 设计，并捐献给 CNCF（云原生计算基金会）维护。简单说，Kubernetes 就像一个**容器管理的操作系统**：开发者只需定义期望状态（我要部署几个容器、每个容器跑什么镜像、需要哪些资源等），Kubernetes 系统就会负责安排容器在集群各节点上运行，并持续监控确保实际状态达到期望状态（这体现了 Kubernetes 的声明式配置和自我修复能力）。

**Kubernetes 的核心概念：**

* **集群 (Cluster)：** 由一组服务器（节点）组成，用来运行 Kubernetes 管理的容器化应用。K8s 将集群中的所有计算资源抽象为一个统一的平台。

* **节点 (Node)：** 集群中的一台服务器（可以是物理机或虚拟机）。分两类：**控制平面 (Control Plane) 节点** 和 **工作节点 (Worker)**。控制平面运行管理调度组件，工作节点运行用户应用容器。K8s 也支持单节点集群。

* **Pod：** Kubernetes 调度的最小单位。一个 Pod 表示一组（通常一个或少数）容器的集合，以及共享网络和存储等上下文。一般每个 Pod 包含一个主要容器，也可以将紧密协作的辅助容器放在同一个 Pod（它们共享 localhost 和卷）。Pod 是短暂的、可替换的实体，有自己的 IP 和端口空间。

* **控制器 (Controller)：** 控制器负责管理 Pod 等对象的生命周期，确保系统达到所需状态。例如 Deployment 控制器负责根据模板创建/销毁Pod，保持一定数量运行；StatefulSet 控制器管理有状态应用的Pod；DaemonSet 确保每个节点上有一个Pod等。

* **Service：** 服务为一组 Pod 提供一个稳定的接入端口和可变的Pod IP之间的负载均衡。因为 Pod 会动态增删且IP多变，Service 通过一个虚拟IP（ClusterIP）和DNS名，持续映射到后端实际Pod上，从而为客户端提供稳定接口。

* **ConfigMap 和 Secret：** 用于将配置数据和敏感信息以解耦的形式提供给 Pod，而不需把这些配置硬编码进镜像。ConfigMap通常存非敏感配置信息，Secret用于敏感数据（会base64加密存储，可选启用K8s加密方案保护）。

* **Volume：** K8s Pod对存储的抽象，可以将节点上的目录、网络存储或云盘等挂载到 Pod 内部，提供持久存储。使用 PersistentVolume (PV) 和 PersistentVolumeClaim (PVC) 机制可实现与底层存储解耦的持久卷分配。

* **调度 (Scheduling)：** Kubernetes 的调度器负责将新建的 Pod 分配到哪个节点运行。调度考虑资源请求（CPU/Mem）、节点标签和污点、亲和性/反亲和等策略来做决策。

* **控制平面组件：**
  
  * **API Server：** 集群的统一接口，提供 REST API。kubectl 等所有操作都通过 API Server 与集群交互。 (ChatGPT建议.md)
  
  * **etcd：** 分布式键值存储，保存整个集群的状态数据（包括所有对象的定义和状态）。它是K8s的数据库，要求高可用和一致性。
  
  * **Controller Manager：** 一系列控制器的集合进程，例如节点控制器(监测节点状态)、Deployment控制器等，都在这里循环执行。
  
  * **Scheduler：** 调度器进程，监视未绑定节点的新Pod，决定将其调度到哪个节点。

* **工作节点组件：**
  
  * **kubelet：** 每个节点上运行的代理，负责与API Server通信，接收调度到本节点的Pod规格然后创建容器（通过容器运行时），并定期汇报Pod运行状态回控制平面 (ChatGPT建议.md)。
  
  * **容器运行时 (Container Runtime)：** 运行容器的具体软件，Docker 是早期默认，现常用 containerd、CRI-O 等，通过Kubernetes的 CRI 接口与 kubelet 集成。
  
  * **kube-proxy：** 每个节点上负责实现 Service 的通信规则（例如设置 iptables 或 ipvs 规则），以在节点上转发请求到正确的Pod (ChatGPT建议.md)。

综上，Kubernetes 采用了**控制器 + 松耦合组件**架构，各组件通过 API Server 交互，以期望状态-实际状态的方式工作。K8s 集群架构可以总结为：多个 Worker Node 提供算力，每个跑着 kubelet 和容器，Master 节点上的 API Server、Scheduler、Controller Manager 共同管理调度 Pod 到各节点，etcd 存储配置和状态 ([Kubernetes - 维基百科，自由的百科全书](https://zh.wikipedia.org/zh-hans/Kubernetes#:~:text=,4%20cAdvisor)) ([Kubernetes - 维基百科，自由的百科全书](https://zh.wikipedia.org/zh-hans/Kubernetes#:~:text=,27))。

初学者可以不必深入每个组件细节，但需要了解 Pod/Service 等对象是什么概念，后续会通过操作理解它们如何运作。

### 3.2 部署 Kubernetes 学习环境

学习 Kubernetes 实际操作，建议先在本地或单台机器上搭建一个**单节点集群**，这样可以方便地使用 kubectl 命令练习各种操作。以下介绍几种简便的方法：

* **Minikube：** 一个工具，可以在本地使用虚拟化启动一个单节点K8s 集群。支持多种后端驱动（如 VirtualBox、Docker 等）。Minikube 包含了所有必要组件，一条命令即可启动。使用方法：安装 minikube 后运行 `minikube start --driver=docker`（如果已装 Docker 则可直接用Docker容器来运行集群）。Minikube 还提供了 `minikube stop` 和 `minikube delete` 来管理生命周期。

* **Kind (Kubernetes-in-Docker)：** 使用 Docker 容器来运行 Kubernetes 控制平面和节点组件的工具。只需 Docker 环境即可使用，可以快速创建一个或多个节点的集群，非常适合在本地测试 K8s 网络、甚至模拟多节点。安装 Kind 后，通过 `kind create cluster` 就能建立集群。

* **K3s：** 由 SUSE Rancher 提供的轻量级 Kubernetes 实现，适合在资源有限环境或边缘设备上运行。可以作为单独学习之用，安装方式简单（curl 脚本一键安装），运行效率高。

* **Docker Desktop 内置 Kubernetes：** 如果使用 Docker Desktop (Windows/Mac)，可以在设置中启用 Kubernetes，一键获得一个单节点集群，kubectl 也会配置好上下文。这对那些环境方便的人来说最简单。

本指南将以 **Minikube** 为例演示。假设已经安装好了 minikube 和 kubectl：
    # 启动一个本地 Kubernetes 集群
    $ minikube start --driver=docker

    😄  minikube v1.xx.xx on Ubuntu
    ✨  Using the docker driver based on user configuration
    👍  Starting control plane node minikube in cluster minikube
    ...
    🌟  Enabling addons: default-storageclass, storage-provisioner
    🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

启动成功后，minikube 已经自动配置好了 `kubectl` 的上下文（通过修改 `~/.kube/config`）。可以验证集群节点和版本：
    $ kubectl get nodes
    NAME       STATUS   ROLES           AGE   VERSION
    minikube   Ready    control-plane   1m    v1.26.1

kubectl 是 Kubernetes 的命令行客户端，通过它可以操作集群上的各种资源（Pod、Service等）。如果没有kubectl，可以通过 `minikube kubectl -- <command>` 代理执行。也可以使用 Kubernetes 仪表盘（dashboard）或其他图形化工具（Lens等）来观察资源状态，但掌握 kubectl 是首要的。

**kubectl 基本用法：**

* 资源类型可以使用单数、复数或缩写（如 pod, pods 或 po 都可以）。

* 常用命令：
  
  * `kubectl get <资源类型> [资源名]`：列出资源或查看某特定资源简要信息。
  
  * `kubectl describe <资源类型> <资源名>`：查看资源的详细描述（状态、事件等）。
  
  * `kubectl logs <Pod名> [-c 容器名]`：查看 Pod 中容器日志，-f 选项跟随最新输出。
  
  * `kubectl exec -it <Pod名> -- <命令>`：进入 Pod 中运行命令（通常是shell）。
  
  * `kubectl apply -f <配置文件>`：根据 YAML 配置文件创建或更新资源（部署资源推荐方式）。
  
  * `kubectl delete <资源类型> <名>`：删除资源。
  
  * `kubectl scale <资源类型>/<名> --replicas=N`：伸缩副本数（对 Deployment等资源）。
  
  * `kubectl port-forward <Pod名或Service名> 本地端口:目标端口`：将本地端口映射到集群内Pod/服务，方便访问。

**命名空间 (Namespace)：** Kubernetes 支持在逻辑上隔离资源，称为命名空间。默认资源都创建在 "default" 命名空间。kubectl 命令可以通过 `-n <namespace>` 指定操作的命名空间。也有全局资源（如节点、存储类等）不属于某个命名空间。

**使用 Minikube 的一些技巧：**

* `minikube dashboard` 可以启动并打开浏览器进入 Kubernetes 仪表盘 UI，方便直观查看资源。

* `minikube service <service名>` 会自动打开该 Service 对应的本地地址（对 NodePort/LoadBalancer类型服务有用）。

* 如果需要使用 LoadBalancer 类型服务，Minikube 可以启用 loadbalancer addon 或使用 `minikube tunnel` 来模拟。

* Minikube 默认启用了 StorageClass 和存储提供器，可以创建 PVC 直接使用。

完成环境准备后，我们就可以对 Kubernetes 集群下发指令，体验其强大的编排功能了。

### 3.3 Pod：部署单个容器

**Pod 是 Kubernetes 调度的基本单位**。尽管一般一个 Pod 只跑一个容器，但理解 Pod 概念很重要，因为 K8s 不直接管理容器，而是通过 Pod 包装。

让我们尝试部署一个最简单的 Pod。可以通过定义 YAML 或者使用 kubectl 命令快捷方式。例如使用命令：
    $ kubectl run nginx-pod --image=nginx:latest --restart=Never
    pod/nginx-pod created

`kubectl run` 这个命令在早期可以直接创建 Deployment 等，现在在 v1.18+ 中主要用来直接创建 Pod（当指定 `--restart=Never` 时，不生成 Deployment）。上面命令创建了一个名字为 nginx-pod 的 Pod，里面运行一个 nginx:latest 容器。

查看 Pod 状态：
    $ kubectl get pods
    NAME        READY   STATUS    RESTARTS   AGE
    nginx-pod   1/1     Running   0          10s

`READY 1/1` 表示这个 Pod 的容器都正常就绪，`STATUS Running` 则说明容器正在运行中。可以用 `kubectl describe pod nginx-pod` 查看详细，包括调度到哪个节点、IP地址、拉取镜像信息、事件日志等。

现在，我们可以尝试访问这个 Pod 运行的 Nginx。因为我们没有创建 Service 暴露它，而且 Pod IP 在集群内部，外部直连不了。不过可以通过 kubectl port-forward 或在 Pod 内执行测试：
    # 方法1: 从集群外部访问Pod，用port-forward把本机端口转发到Pod的80端口
    $ kubectl port-forward pod/nginx-pod 8080:80
    Forwarding from 127.0.0.1:8080 -> 80
    Forwarding from [::1]:8080 -> 80
    # 现在在本机浏览器访问 http://localhost:8080 就相当于访问Pod的80端口了

    # 方法2: 直接在Pod内部用curl访问自身（需要镜像里有curl，这里nginx镜像没有，可以kubectl exec一个有工具的pod）
    $ kubectl exec -it nginx-pod -- /bin/sh
    # 在 Pod 内获得了一个Shell，但这个nginx镜像很简洁没有shell，exec会失败。改用别的busybox Pod测试：
    $ kubectl run tmp --image=busybox:latest -it --rm --restart=Never -- wget -qO- http://nginx-pod

上面第二种方式用了 `--rm` 和 `-it` 直接运行一个临时 Pod 去访问 nginx-pod 服务，可以验证网络通。（由于在同一命名空间，kubectl run 的 Pod 会自动配置 DNS，可以用名字访问。对于直接通过 Pod 名通信，需要 kube-dns服务发现Pod IP，这在没有Headless Service情况下未必能解析Pod名，可以改用 `wget -qO- <nginx-pod的ClusterIP>` 或者先创建一个 Service。）

实际上，上述 kubectl run 创建 Pod 方法在生产中不常用，因为直接创建Pod没有自愈能力。**如果 Pod 挂掉，K8s不会自动重启一个新的**（因为我们指定 restart=Never）。因此，一般生产应用都用 Deployment 等高层抽象来管理 Pod 副本。本节作为理解 Pod 基础，先用这种方式体验。

**删除 Pod：**
    $ kubectl delete pod nginx-pod
    pod "nginx-pod" deleted

删除操作会通知 kubelet优雅终止容器，默认有 termination-grace-period（30秒）等待容器退出，否则强杀。

**Pod YAML 定义：** 为了打牢概念，这里给出 Pod 对象的 YAML 示例：
    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx-pod
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
          resources:
            limits:
              cpu: "0.5"
              memory: "256Mi"
          livenessProbe:
            httpGet:
              path: /
              port: 80
            initialDelaySeconds: 30
            periodSeconds: 10

这个 YAML 描述了一个 Pod 包含 nginx 容器，暴露80端口，限制 CPU 0.5核、内存256Mi，并配置了存活探针（liveness probe）来定期HTTP检查容器健康（如果连续失败K8s将重启容器）。这一切用 kubectl 都可以 `apply -f` 创建。由于稍复杂，不展开执行，重点理解元素即可。

### 3.4 Deployment：管理多副本应用

单个 Pod 不够健壮——它挂了不会自动替换。因此 Kubernetes 提供了 **Deployment（部署）** 这种高级资源，来管理一组 Pod 副本（副本集ReplicaSet）。Deployment 控制器确保系统始终有指定数量的 Pod 运行，并支持滚动更新、回滚等发布特性。

**创建 Deployment：** 可以用 YAML 或 kubectl 命令 `kubectl create deploy` 来创建。这里用命令方便：
    $ kubectl create deployment nginx-dep --image=nginx:1.21-alpine --replicas=3
    deployment.apps/nginx-dep created

这会创建一个 Deployment 名为 nginx-dep，使用镜像 nginx:1.21-alpine，期望3个副本。Deployment 创建时会自动创建一个同名的 ReplicaSet（副本集），然后ReplicaSet再创建3个 Pod 副本。可以查看各资源：
    $ kubectl get deployments
    NAME         READY   UP-TO-DATE   AVAILABLE   AGE
    nginx-dep    3/3     3            3           10s

    $ kubectl get rs
    NAME                   DESIRED   CURRENT   READY   AGE
    nginx-dep-5c86fbc7d7   3         3         3       10s

    $ kubectl get pods -l app=nginx-dep
    NAME                         READY   STATUS    RESTARTS   AGE
    nginx-dep-5c86fbc7d7-abcde   1/1     Running   0          10s
    nginx-dep-5c86fbc7d7-fghij   1/1     Running   0          10s
    nginx-dep-5c86fbc7d7-klmno   1/1     Running   0          10s

通过 labels 选择器可以批量获取相关 Pod。Deployment 默认会给 Pod 加上 `app=<deployment名>` 的标签，我们也可以自己在 Deployment 模板中定义标签。无论如何，Deployment 通过标签和ReplicaSet关联Pod（ReplicaSet有一个selector匹配这些标签）。

**Scaling 伸缩：** 我们可以轻松伸缩 Deployment：
    $ kubectl scale deployment nginx-dep --replicas=5
    deployment.apps/nginx-dep scaled

    $ kubectl get pods -l app=nginx-dep
    NAME                         READY   STATUS    RESTARTS   AGE
    nginx-dep-5c86fbc7d7-abcde   1/1     Running   0          1m
    nginx-dep-5c86fbc7d7-fghij   1/1     Running   0          1m
    nginx-dep-5c86fbc7d7-klmno   1/1     Running   0          1m
    nginx-dep-5c86fbc7d7-xyz12   1/1     Running   0          5s
    nginx-dep-5c86fbc7d7-uvw34   1/1     Running   0          5s

新的两个 Pod 很快被创建起来。K8s 调度器会找集群中有空余资源的节点跑它们（minikube 单节点就都在本机）。如果把副本数缩回3，则会终止多余的Pod（具体终止哪个由ReplicaSet/Deployment控制，通常按控制器自定义逻辑比如优先删除最老/最先启动的Pod）。

**滚动更新 (Rolling Update)：** Deployment 支持无停机升级应用。例如我们将镜像从1.21-alpine更新到1.23-alpine：
    $ kubectl set image deployment/nginx-dep nginx=nginx:1.23-alpine
    deployment.apps/nginx-dep image updated

观察 Deployment 状态：
    $ kubectl rollout status deployment/nginx-dep
    Waiting for deployment "nginx-dep" rollout to finish: 2 out of 5 new pods have been updated...
    ...
    deployment "nginx-dep" successfully rolled out

Kubernetes 会按一定策略（默认 maxSurge=25%, maxUnavailable=25%）滚动更新Pod：先创建新的Pod，再杀掉旧的，一批一批进行，保证有大部分服务始终可用。我们可以 `kubectl get rs` 看到此时出现了两个 ReplicaSet：一个对应旧版本Pod还剩2，另一个新ReplicaSet对应新版本Pod已有3。当更新完成，旧ReplicaSet就scale为0但仍留存历史记录（Deployment保留最后几版历史以支持回滚）。

**回滚：** 若发现新版有问题，可执行 `kubectl rollout undo deployment/nginx-dep` 回滚到上一版本，它会重启原来的镜像。可以通过 `kubectl rollout history deployment/nginx-dep` 查看历史版本信息，包括 revision代号。

**暂停/继续：** `kubectl rollout pause deployment/nginx-dep` 可以暂停Deployment的自动更新，用于先修改多个属性再统一恢复应用，以防止中间状态。修改完执行 `kubectl rollout resume deployment/nginx-dep` 恢复滚动。

**删除 Deployment：** 当不再需要，`kubectl delete deployment nginx-dep` 会删除Deployment和其创建的ReplicaSet及Pod。

**练习：**

* 创建一个 Deployment，运行 httpd (Apache) 容器副本3个。然后用 `kubectl port-forward` 将任一Pod的80端口映射到本地8080，访问几次网页，观察每次返回的Pod主机名（可以在Pod里配置环境变量或modify httpd welcome page包含hostname）。因为port-forward固定连一个Pod，页面源不会变。之后尝试创建一个 Service 来统一暴露这3个副本，在集群内部访问Service IP，多次请求负载均衡在不同Pod（下一节Service会细讲）。

* 模拟 Pod 故障：删除 Deployment 某一个 Pod，观察 Deployment 会自动创建新 Pod 补齐。然后模拟节点故障（如果是minikube单节点，可以停掉 kubelet 服务但minikube不容易模拟这种，略）。了解 Deployment/ReplicaSet保证副本数的机制。

* 修改 Deployment 资源限制，例如给容器加资源 requests 和 limits（可编辑 Deployment：`kubectl edit deployment nginx-dep`），然后观察 Pod 是否重建（资源限制改变会导致重新调度Pod）。

Deployment 是 Kubernetes 中最常见的工作负载类型之一，适合无状态应用。对于有状态应用或需要有序部署/独立标识的Pod，则需使用 StatefulSet；对于每节点一个Pod的情况用 DaemonSet。本指南不详述后两者，但可在实际场景中探索使用。

### 3.5 Service：服务发现与负载均衡

上节提到，通过 Deployment 我们获得了一组 Pod 副本，但 Pod 的IP可能变化且不固定数量。**Service** 对象为一组Pod提供了一个固定的访问入口和名称，使客户端无需直接感知Pod的动态变化。Service 主要有以下作用：

* **稳定的虚拟 IP (ClusterIP)：** Kubernetes 默认会给每个Service分配一个集群内部可访问的IP地址（从一个专用网段，通常10.x.x.x）。集群内其他Pod或组件只要访问这个IP就相当于访问服务，无需关心后端Pod IP。

* **DNS 名称：** Kubernetes 内建DNS服务器（如 CoreDNS），会为Service创建同名的DNS A记录（<服务名>.<命名空间>.svc.cluster.local），方便通过名称访问Service。

* **负载均衡：** Service 会将进来的请求根据一定策略分发到其后端的Pod上，实现负载均衡。cluster内部基于 kube-proxy 一般用iptables/ipvs转发流量。

* **服务发现：** Pod 可以通过环境变量或DNS自动发现服务。K8s会将同一Namespace下的Service地址以环境变量注入到Pod，但这种方法已不太推荐，DNS方式更灵活。

Service 有多种类型：

* **ClusterIP**（默认）：只分配内部IP，集群外部无法直接访问。通常后端应用的内部服务采用ClusterIP，由前端或Ingress代理访问。

* **NodePort：** 在每个节点上开放一个端口，映射到Service。这样集群外部可以通过访问`<任意节点IP>:<NodePort>`来访问服务。这种方式简单但端口范围有限(30000-32767默认)且需自行处理高可用（任一节点挂了还可用其他节点IP）。

* **LoadBalancer：** 在支持的云环境下（如AWS、GCP、Azure）会自动创建云负载均衡器，将流量导向集群节点上的Service。这对用户透明，而且LB提供一个稳定外部IP。Minikube则会在本地为LoadBalancer创建一个进程代理或需要使用 `minikube tunnel` 来获得一个主机上的负载均衡IP。

* **Headless Service：** 如果不需要负载均衡，只想利用DNS发现Pod列表，可以创建 clusterIP=None 的 service，不会分配IP，而会为每个后端Pod创建DNS A记录。这常用于需要客户端自己做LB或者需要直接知道各Pod地址的场景，如数据库集群的主从节点发现等。

**创建 Service：** 可以通过 YAML 或 kubectl expose 命令。例如继续使用前述 nginx-dep Deployment，创建一个 ClusterIP Service 来覆盖其 Pod：
    $ kubectl expose deployment nginx-dep --port=80 --target-port=80 --name nginx-service
    service/nginx-service exposed

`kubectl expose` 通过已有对象创建Service：它自动根据 Deployment 的 label selector 来关联 Pod（具体看 Deployment's Pod模板的 labels）。--port 指服务暴露端口，--target-port 指后端Pod端口（如果一致可省略）。现在查看 Service：
    $ kubectl get service nginx-service
    NAME            TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
    nginx-service   ClusterIP   10.96.182.54   <none>        80/TCP    5s

可以看到 Service 拥有一个 ClusterIP 10.96.182.54（集群内部IP段），没有 External-IP（因为不是LoadBalancer），端口80。

要测试Service，可以在集群内发请求：
    $ kubectl run curlpod --rm -it --image=curlimages/curl:latest --restart=Never -- \
          curl -I nginx-service.default.svc.cluster.local
    HTTP/1.1 200 OK
    Server: nginx/1.23.4
    Date: Tue, 22 Apr 2025 09:50:00 GMT
    ...

上面用一个临时容器执行 curl 命令，访问 Service DNS（也可以用 `curl nginx-service` 简写，因为在default命名空间，会自动搜索 default.svc）。返回 200 OK 证明成功。多次执行 curl，可看到命中不同 Pod（如果Nginx输出了pod信息我们能区分，这里略）。

**NodePort 示例：** 如果需要让 Minikube 主机访问，可以创建 NodePort 类型：
    $ kubectl expose deployment nginx-dep --type=NodePort --port=80 --name nginx-nodeport
    service/nginx-nodeport exposed
    $ kubectl get svc nginx-nodeport
    NAME             TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
    nginx-nodeport   NodePort   10.96.255.100   <none>        80:31555/TCP   5s

这里 NodePort 映射出了31555端口。Minikube 环境下，可以通过 `minikube service nginx-nodeport --url` 获取访问URL，比如 `http://127.0.0.1:31555`. 用浏览器访问即可。

**LoadBalancer 示例（Minikube 环境）：** minikube提供 `minikube tunnel` 可捕获 LoadBalancer 类型的IP到本地主机。比如：
    $ kubectl expose deployment nginx-dep --type=LoadBalancer --port=80 --name nginx-lb
    service/nginx-lb exposed
    $ kubectl get svc nginx-lb
    NAME        TYPE           CLUSTER-IP     EXTERNAL-IP    PORT(S)        AGE
    nginx-lb    LoadBalancer   10.96.20.143   10.96.20.143   80:32377/TCP   10s

Minikube此时给了一个和ClusterIP一样的 External-IP（可能等待 tunnel）。运行 `minikube tunnel` 后再查，会获得一个类似 127.0.0.1 或主机IP的 external IP，然后就可访问。云环境则LB IP为云分配的公共IP。

**Service selector 和 endpoints：** Service 通常通过 `spec.selector` 来选择后端Pod（依据标签）。也可以手动指定 endpoints（很少用）。`kubectl describe svc <name>` 可以看到其选中的 Pod 列表（Endpoints段）。此外 `kubectl get endpoints` 资源会列出每个Service当前关联的Pod IP和端口。Service 会持续监控符合selector的Pod变化，自动更新端点。

**Ingress（入口）：** 提到对外访问，不得不提 Ingress。Ingress并不是Service类型，而是一种集群入口资源，它通过集成的 **Ingress Controller**（如 Nginx ingress controller、Traefik 等）来工作。Ingress允许根据HTTP请求的域名和路径，将流量转发到不同Service，实现反向代理和简易的应用层负载。由于Ingress配置和Controller部署较复杂，这里不细讲。Minikube可以开启 ingress addon 来使用。Ingress是更灵活的对外暴露方式，掌握Service后可自行学习Ingress的配置规则。

**练习：**

* 在 Kubernetes 集群部署一个简单的 Echo 服务器（可以使用 ealen/echo-server 镜像，该服务会把请求信息原样返回）。创建 Deployment 后，为其创建一个 ClusterIP Service。然后在另一个Pod内访问，观察返回内容（包含了服务器hostname即Pod名，可验证LB效果）。

* 将上面的 Service 改为 NodePort 或 LoadBalancer，直接从宿主或外部访问 echo 服务。尝试同时启动多个并发请求，确认能均匀分发。

* 学习 Headless Service：创建一个带有 StatefulSet 的应用（如 3 个副本的简易 DNS 工具容器 busybox），为它创建一个 `clusterIP: None` 的 Service。然后使用 `nslookup` 或 `dig` 在集群内解析这个 Service DNS，看看是否返回所有 Pod IP 列表。了解这对有状态服务的意义。

Service 是 Kubernetes 网络的基石，它解除了 Pod 动态变化对客户端造成的困扰，让我们可以像使用固定服务一样访问容器工作负载。随着学习深入，你还会遇到 NetworkPolicy 控制流量策略，Service Mesh 进一步增强流量治理等概念，但最核心的Service/Pod机制一定要熟练掌握。

### 3.6 ConfigMap 与 Secret：配置与密钥管理

在实际应用中，我们常需要将一些配置参数提供给容器，比如应用配置文件、命令行参数，或者敏感信息如数据库密码、API密钥等。将这些配置直接写死在镜像或Deployment中既不灵活又不安全。Kubernetes 提供了 **ConfigMap** 和 **Secret** 两种资源来分别管理非敏感配置和敏感信息。

**ConfigMap：** 存储非敏感的键值对配置。可以把 ConfigMap 理解为一个字典或配置文件容器。我们可以把应用的配置项抽取到 ConfigMap，在 Pod 模板中引用它，使 Pod 启动时从 ConfigMap 读取配置值。

**Secret：** 和 ConfigMap 类似，但专门用于敏感数据（如密码、证书）。Secret 中的数据会进行 base64 编码存储，可以选配启用EncryptionConfiguration让etcd中加密。不过要注意 base64只是编码非加密，默认Secret数据在API返回时还是可Base64解码的，所以启用Encryption或外部密钥管理才更安全。

**提供配置给 Pod 的方式：**

1. **作为环境变量：** 可以将 ConfigMap/Secret 的某个键值注入Pod内的环境变量。

2. **作为挂载文件：** ConfigMap 和 Secret 都可以以**卷 (Volume)** 方式挂载进容器文件系统。ConfigMap里的每个键会成为一个文件（文件名为键，内容为值）。Secret类似，每个键是文件，值是解码后的数据。常用于提供配置文件或证书文件。

3. **命令参数引用：** 在 Pod spec的 args/command 字段中，可以使用占位符从 ConfigMap/Secret 引用值（通过 env 或 volumes 实现更通用）。

**创建 ConfigMap/Secret：** 可以用 YAML 定义或 kubectl 命令直接从文件创建。

例如，有一个配置文件 app.conf：
    MODE=production
    TIMEOUT=30

创建 ConfigMap 可以：
    $ kubectl create configmap myapp-config --from-file=app.conf
    configmap/myapp-config created

这样 ConfigMap 有一个键 `app.conf` 对应内容为文件内容。也可以用 `--from-literal=MODE=production --from-literal=TIMEOUT=30` 创建键值。

创建 Secret 示例：
    $ kubectl create secret generic db-secret --from-literal=username=root --from-literal=password=Pa$$w0rd
    secret/db-secret created

这样会生成Secret，里面包含键 username 和 password，其值被base64存储。可以用 `kubectl get secret db-secret -o yaml` 看内容（会显示base64编码）。

**将 ConfigMap 挂载为文件：** 在 Pod spec 中：
        volumes:
          - name: app-config-vol
            configMap:
              name: myapp-config   # 引用上面创建的 ConfigMap
        containers:
        - name: myapp
          image: busybox
          volumeMounts:
            - name: app-config-vol
              mountPath: "/etc/myapp"    # 将 ConfigMap 内容挂载到这个目录
              readOnly: true

这样 ConfigMap 里的每个键会成为 /etc/myapp/ 下的文件。例如 app.conf 会变成 /etc/myapp/app.conf，文件内容就是原内容。

**将 Secret 挂载为文件：**
        volumes:
          - name: db-secret-vol
            secret:
              secretName: db-secret
        containers:
        - name: db-client
          image: mysql:5.7
          volumeMounts:
            - name: db-secret-vol
              mountPath: "/run/secrets" 
              readOnly: true

这样 /run/secrets/username 和 /run/secrets/password 文件内分别是 root 和 Pa$$w0rd。然后应用可以读取这些文件获取敏感信息。

**通过环境变量提供：**
        containers:
        - name: myapp
          image: myapp:1.0
          env:
            - name: APP_MODE
              valueFrom:
                configMapKeyRef:
                  name: myapp-config
                  key: MODE
            - name: DB_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: db-secret
                  key: password

上面 Pod 中myapp容器会得到 APP_MODE 环境变量为 "production"，DB_PASSWORD 为 "Pa$$w0rd"。

当 ConfigMap 或 Secret 更新时，挂载为 volume 的文件内容会自动更新到 Pod 内（大约周期性间隔或通过inotify），不过环境变量方式注入的在 Pod 生命周期内不会改变（因为那是在启动进程前设置的，不会动态感知）。

**配置更新的处理：** ConfigMap 更新自动反映到Volume挂载内容，但 Pod 本身不会重启。如果配置改变需要Pod重启加载，可以通过部署新的版本或者触发 rollout。例如修改 ConfigMap 后，可以触发 Deployment的 annotation 变化，让K8s重建Pod使用新配置。（一些工具如 Reloader operator 可自动实现这个）。

**敏感信息注意：** K8s Secret默认以base64编码存储，只算轻微隐藏。APIServer对Secret做访问控制，可以RBAC限制谁能get secret。但在节点上运行的 Pod 如果有权限挂载Secret，就可读到里面明文数据。所以还需配合密文存储方案或外部密钥管理服务（KMS）如果对安全要求高。

**练习：**

* 创建一个简单应用，打印环境变量或读取文件。可以用 busybox as base, command: ["sh","-c","echo DB_PASS: $DB_PASS && cat /run/secrets/token"].然后准备一个 ConfigMap 或 Secret 提供 DB_PASS env和token文件。部署Pod验证能否正确读到。

* 修改 ConfigMap 的值，例如改变APP_MODE=debug，看已经在运行的 Pod 挂载文件是否更新（shell进入容器查看文件）。然后滚动重启Pod（如 Deployment rollout restart）让环境变量也更新。

* 尝试用 kubectl 来更新 Secret （可以 `kubectl edit secret db-secret` 修改base64值），注意查看 Pod 是否能无缝拿到新Secret内容（如果通过Volume挂载，则文件更新；环境变量则需要重启Pod才能生效新的secret）。

通过 ConfigMap 和 Secret，我们实现了应用配置与容器镜像的解耦，可以在不同环境下重用相同镜像，通过注入不同配置来改变行为。这符合12-factor应用理念，使得部署更加灵活、安全。

### 3.7 实战：部署应用并调试

这一节，我们综合运用前面所学，通过一个示例完整演练 Kubernetes 部署和调试过程。设想一个典型场景：我们要在 Kubernetes 上部署一个简单的 Web 应用（比如 Python Flask 应用），连接一个后端数据库服务。我们将经历创建 Deployment、Service、ConfigMap/Secret、查看日志、排障的过程。

**应用背景：** 一个 Flask 应用提供 `/hello` 接口，返回一个问候语和访问计数，计数存储在 Redis 数据库。我们将部署 Flask 应用容器和 Redis 容器，各自为Deployment，并配置 Service 让 Flask 能连接 Redis。Flask 的 Redis 地址和凭证通过 ConfigMap/Secret 注入。然后模拟一些错误场景来调试。

_注：由于时间篇幅，假定 Flask 应用镜像 `myflask:1.0` 已经打包包含代码。_

**步骤1：部署 Redis**
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: redis-deploy
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: redis
      template:
        metadata:
          labels:
            app: redis
        spec:
          containers:
          - name: redis
            image: redis:6.2-alpine
            ports:
            - containerPort: 6379
            env:
            - name: REDIS_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: redis-secret
                  key: password
            args: ["redis-server", "--requirepass", "$(REDIS_PASSWORD)"]
    ---
    apiVersion: v1
    kind: Secret
    metadata:
      name: redis-secret
    type: Opaque
    data:
      password: c29tZVBhc3M=   # base64 for "somePass"
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: redis-service
    spec:
      selector:
        app: redis
      clusterIP: None   # headless service, so we can access pod directly if needed
      ports:
      - port: 6379
        targetPort: 6379

以上 YAML 定义：Redis Deployment一份，副本1；Secret 存储密码somePass；Redis启动命令带上密码；Service暴露Redis端口。我们用了 Headless Service (clusterIP: None) 主要是为了示范不同类型，其实这里普通ClusterIP也行。应用会通过`redis-service:6379`访问Redis。

应用前，先 kubectl apply 创建Secret，然后 Deployment & Service。

**步骤2：部署 Flask 应用**
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: flask-deploy
    spec:
      replicas: 2
      selector:
        matchLabels:
          app: flask
      template:
        metadata:
          labels:
            app: flask
        spec:
          containers:
          - name: flask-app
            image: myflask:1.0
            ports:
            - containerPort: 5000
            env:
            - name: REDIS_HOST
              value: "redis-service"    # 对应上面Service名称
            - name: REDIS_PORT
              value: "6379"
            - name: REDIS_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: redis-secret
                  key: password
            - name: APP_MODE
              valueFrom:
                configMapKeyRef:
                  name: flask-config
                  key: mode
    ---
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: flask-config
    data:
      mode: "production"
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: flask-service
    spec:
      selector:
        app: flask
      ports:
      - port: 80
        targetPort: 5000
      type: NodePort   # 方便外部访问

这里 Flask Deployment 用2副本，通过环境变量读取 Redis 服务地址、密码和自身模式（例如APP_MODE控制日志级别什么的）。创建相应的 ConfigMap 和 Service（NodePort让我们本地能访问80->NodePort转5000）。

Apply 以上 YAML 后，检查各资源：
    $ kubectl get deploy
    NAME            READY   UP-TO-DATE   AVAILABLE   AGE
    flask-deploy    2/2     2            2           30s
    redis-deploy    1/1     1            1           1m

    $ kubectl get pods -o wide
    NAME                           READY   STATUS    NODE      IP           ...
    flask-deploy-...-abcde         1/1     Running   minikube  172.17.0.10
    flask-deploy-...-fghij         1/1     Running   minikube  172.17.0.11
    redis-deploy-...-xyz12         1/1     Running   minikube  172.17.0.9

    $ kubectl get svc
    NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
    flask-service   NodePort    10.96.150.50    <none>        80:30080/TCP   30s
    redis-service   ClusterIP   None            <none>        6379/TCP       1m

Flask service NodePort是30080（Minikube可以 minikube service flask-service 打开）。现在测试访问：
    $ curl http://localhost:30080/hello
    Hello, visitor! You are number 1

    $ curl http://localhost:30080/hello
    Hello, visitor! You are number 2

访问计数递增，说明Flask正确连接Redis存储计数。若返回错误，则需要排查：

**排障示例：** 假设我们请求时得到了 500 错误或超时。如何定位？

1. 用 `kubectl get pods` 看 Pod 是否都 Running，若 CrashLoopBackOff 可能应用启动失败。
   
   * 用 `kubectl logs <flask-pod>` 查看错误日志。若日志提示连接拒绝，可能 Redis 服务没连接上。
   
   * 检查 Flask Pod 的环境变量设置：`kubectl exec <flask-pod> -- printenv | grep REDIS` 看是否正确。
   
   * 检查 Redis Service 是否正常：`kubectl get endpoints redis-service` 应有1个IP。
   
   * 从 Flask Pod 内尝试 ping 或 nc redis-service:6379。
   
   * 如果密码错，会报鉴权失败，可检查 Secret 的值与 Redis配置是否匹配。

2. 如果Pod没启动成功，describe pod 查看事件。例如 ImagePullBackOff 表示镜像拉取失败，需检查镜像名或仓库凭据；CrashLoop表示应用异常退出，查看 logs 或 describe 中的 "Last State: Terminated: Exit Code".

3. 如果只是部分请求失败，有可能一部分Pod正常，一部分有问题。可以通过 `kubectl logs` 每个Pod分别看。如果发现某Pod日志不断出现错误，可 `kubectl delete pod` 删除，让Deployment重建一个新的，也许就绪（这种不根本的需要调代码解决，但K8s确保了临时问题通过重启自愈）。

**监控应用状态：**

* `kubectl get deployment flask-deploy -w` 可以实时看到副本ready变化。

* 给 Deployment 配置 `livenessProbe` 和 `readinessProbe` 来自动检测并处理异常Pod，比如自动重启无响应的应用。

* 使用 `kubectl top pods`（需要 Metrics Server 安装）可以查看资源使用，以防超出requests导致Pod被驱逐(OOMKill等)。

* Logging 和 Monitoring 方面，建议集成EFK日志收集、Prometheus度量监控等。

**练习延伸：**

* 故意配置一个错误，例如把 Flask Deployment 的 REDIS_PASSWORD 改错，然后观察应用日志错误并修复。

* 尝试给 Flask Deployment 添加 readinessProbe（HTTP GET /hello）和 livenessProbe（TCP port 5000），然后观察 describe pod 中Probe状态，测试kill应用进程触发liveness重新启动（需要shell进Pod kill -9，模拟进程挂掉）。

* 扩展：给 flask-service 配一个 Ingress，通过域名 host 路由，使其从80 NodePort改为Ingress管理访问。

通过这个综合练习，我们完整体验了 Kubernetes 下部署一个应用涉及的各方面：定义资源 -> 验证运行 -> 排查故障 -> 调整配置。实战中，还需要掌握**升级**（如镜像新版本通过 Deployment 滚动更新，如把 Flask换版本、DB换版本的步骤）和**维护**（监控指标，日志收集，资源扩容等）。但有了基本概念和操作能力后，进一步学习特定工具和插件将更容易。
第四部分：OpenStack 云平台基础
--------------------

学习完容器编排领域的 Kubernetes 后，我们将目光转向另一个重要的云计算平台：**OpenStack**。OpenStack 是一个开源的云基础设施管理平台，主要用于构建和管理私有云/公有云的数据中 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=OpenStack%E6%98%AF%E4%B8%80%E4%B8%AA%E8%87%AA%E7%94%B1%E3%80%81%E5%BC%80%E6%BA%90%E7%9A%84%E4%BA%91%E8%AE%A1%E7%AE%97%E5%B9%B3%E5%8F%B0%E3%80%82%E5%AE%83%E4%B8%BB%E8%A6%81%E4%BD%9C%E4%B8%BA%E5%9F%BA%E7%A1%80%E8%AE%BE%E6%96%BD%E5%8D%B3%E6%9C%8D%E5%8A%A1%EF%BC%88IaaS%EF%BC%89%E9%83%A8%E7%BD%B2%E5%9C%A8%E5%85%AC%E7%94%A8%E4%BA%91%E5%92%8C%E7%A7%81%E6%9C%89%E4%BA%91%E4%B8%AD%EF%BC%8C%E6%8F%90%E4%BE%9B%E8%99%9A%E6%8B%9F%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%92%8C%E5%85%B6%E4%BB%96%E8%B5%84%E6%BA%90%E7%BB%99%E7%94%A8%E6%88%B7%E4%BD%BF%E7%94%A8%E3%80%82%E8%AF%A5%E8%BD%AF%E4%BB%B6%E5%B9%B3%E5%8F%B0%E7%94%B1%E7%9B%B8%E4%BA%92%20%E5%85%B3%E8%81%94%E7%9A%84%E7%BB%84%E4%BB%B6%E7%BB%84%E6%88%90%EF%BC%8C%E6%8E%A7%E5%88%B6%E7%9D%80%E6%95%B4%E4%B8%AA%E6%95%B0%E6%8D%AE%E4%B8%AD%E5%BF%83%E5%86%85%E4%B8%8D%E5%90%8C%E7%9A%84%E5%8E%82%E5%95%86%E7%9A%84%E8%AE%A1%E7%AE%97%E3%80%81%E5%AD%98%E5%82%A8%E5%92%8C%E7%BD%91%E7%BB%9C%E8%B5%84%E6%BA%90%E7%9A%84%E7%A1%AC%E4%BB%B6%E6%B1%A0%E3%80%82%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E5%9F%BA%E4%BA%8E%E7%BD%91%E7%BB%9C%E7%9A%84%E4%BB%AA%E8%A1%A8%E7%9B%98%E3%80%81%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%E6%88%96RESTful%E7%BD%91%E7%BB%9C%E6%9C%8D%E5%8A%A1%E6%9D%A5%E7%AE%A1%E7%90%86%E3%80%82))-L4】本章节将介绍 OpenStack 的核心组件、基本操作和运维要点。虽然 OpenStack 本身不直接运行容器（它主要管理虚拟机等资源），但作为云原生运维工程师，我们常需要对底层云基础设施有所了解。OpenStack 技能有助于我们构建私有云环境，或在云计算IaaS层面从事运维工作。

### 4.1 OpenStack 简介与架构

**OpenStack 是什么？** 根据资料，OpenStack 是一个自由开源的云计算平台，主要提供基础设施即服务 (Ia ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=OpenStack%E6%98%AF%E4%B8%80%E4%B8%AA%E8%87%AA%E7%94%B1%E3%80%81%E5%BC%80%E6%BA%90%E7%9A%84%E4%BA%91%E8%AE%A1%E7%AE%97%E5%B9%B3%E5%8F%B0%E3%80%82%E5%AE%83%E4%B8%BB%E8%A6%81%E4%BD%9C%E4%B8%BA%E5%9F%BA%E7%A1%80%E8%AE%BE%E6%96%BD%E5%8D%B3%E6%9C%8D%E5%8A%A1%EF%BC%88IaaS%EF%BC%89%E9%83%A8%E7%BD%B2%E5%9C%A8%E5%85%AC%E7%94%A8%E4%BA%91%E5%92%8C%E7%A7%81%E6%9C%89%E4%BA%91%E4%B8%AD%EF%BC%8C%E6%8F%90%E4%BE%9B%E8%99%9A%E6%8B%9F%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%92%8C%E5%85%B6%E4%BB%96%E8%B5%84%E6%BA%90%E7%BB%99%E7%94%A8%E6%88%B7%E4%BD%BF%E7%94%A8%E3%80%82%E8%AF%A5%E8%BD%AF%E4%BB%B6%E5%B9%B3%E5%8F%B0%E7%94%B1%E7%9B%B8%E4%BA%92%20%E5%85%B3%E8%81%94%E7%9A%84%E7%BB%84%E4%BB%B6%E7%BB%84%E6%88%90%EF%BC%8C%E6%8E%A7%E5%88%B6%E7%9D%80%E6%95%B4%E4%B8%AA%E6%95%B0%E6%8D%AE%E4%B8%AD%E5%BF%83%E5%86%85%E4%B8%8D%E5%90%8C%E7%9A%84%E5%8E%82%E5%95%86%E7%9A%84%E8%AE%A1%E7%AE%97%E3%80%81%E5%AD%98%E5%82%A8%E5%92%8C%E7%BD%91%E7%BB%9C%E8%B5%84%E6%BA%90%E7%9A%84%E7%A1%AC%E4%BB%B6%E6%B1%A0%E3%80%82%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E5%9F%BA%E4%BA%8E%E7%BD%91%E7%BB%9C%E7%9A%84%E4%BB%AA%E8%A1%A8%E7%9B%98%E3%80%81%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%E6%88%96RESTful%E7%BD%91%E7%BB%9C%E6%9C%8D%E5%8A%A1%E6%9D%A5%E7%AE%A1%E7%90%86%E3%80%82))-L4】它由一系列相互关联的组件构成，控制着数据中心里的计算、存储和网络资源池，用户可以通过Web界面、命令行或API来管理 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=OpenStack%E6%98%AF%E4%B8%80%E4%B8%AA%E8%87%AA%E7%94%B1%E3%80%81%E5%BC%80%E6%BA%90%E7%9A%84%E4%BA%91%E8%AE%A1%E7%AE%97%E5%B9%B3%E5%8F%B0%E3%80%82%E5%AE%83%E4%B8%BB%E8%A6%81%E4%BD%9C%E4%B8%BA%E5%9F%BA%E7%A1%80%E8%AE%BE%E6%96%BD%E5%8D%B3%E6%9C%8D%E5%8A%A1%EF%BC%88IaaS%EF%BC%89%E9%83%A8%E7%BD%B2%E5%9C%A8%E5%85%AC%E7%94%A8%E4%BA%91%E5%92%8C%E7%A7%81%E6%9C%89%E4%BA%91%E4%B8%AD%EF%BC%8C%E6%8F%90%E4%BE%9B%E8%99%9A%E6%8B%9F%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%92%8C%E5%85%B6%E4%BB%96%E8%B5%84%E6%BA%90%E7%BB%99%E7%94%A8%E6%88%B7%E4%BD%BF%E7%94%A8%E3%80%82%E8%AF%A5%E8%BD%AF%E4%BB%B6%E5%B9%B3%E5%8F%B0%E7%94%B1%E7%9B%B8%E4%BA%92%20%E5%85%B3%E8%81%94%E7%9A%84%E7%BB%84%E4%BB%B6%E7%BB%84%E6%88%90%EF%BC%8C%E6%8E%A7%E5%88%B6%E7%9D%80%E6%95%B4%E4%B8%AA%E6%95%B0%E6%8D%AE%E4%B8%AD%E5%BF%83%E5%86%85%E4%B8%8D%E5%90%8C%E7%9A%84%E5%8E%82%E5%95%86%E7%9A%84%E8%AE%A1%E7%AE%97%E3%80%81%E5%AD%98%E5%82%A8%E5%92%8C%E7%BD%91%E7%BB%9C%E8%B5%84%E6%BA%90%E7%9A%84%E7%A1%AC%E4%BB%B6%E6%B1%A0%E3%80%82%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E5%9F%BA%E4%BA%8E%E7%BD%91%E7%BB%9C%E7%9A%84%E4%BB%AA%E8%A1%A8%E7%9B%98%E3%80%81%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%E6%88%96RESTful%E7%BD%91%E7%BB%9C%E6%9C%8D%E5%8A%A1%E6%9D%A5%E7%AE%A1%E7%90%86%E3%80%82))-L4】。简单来说，OpenStack可以让我们像使用AWS EC2那样，在自己的数据中心上搭建类似的云服务：创建虚拟机、分配网络和存储等等。

OpenStack 最早由 NASA 和 Rackspace 合作发起于2010年，经过多年的社区发展，如今包含超过50个子项目组件（核心组件+周边服务）。完整安装OpenStack较为复杂，但理解其主要模块及架构对于运维是必要的。

**OpenStack 核心服务组件：** 通常按功能分为计算、网络、存储、身份等 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=%E6%A0%B8%E5%BF%83%E7%BB%84%E4%BB%B6%EF%BC%9A%E4%B8%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%2F%E5%AE%9E%E4%BE%8B%E6%8F%90%E4%BE%9B%E6%9C%8D%E5%8A%A1)) ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=))236】：

* **Keystone（身份服务）**：负责认 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=%E5%85%A8%E5%B1%80%E7%BB%84%E4%BB%B6%EF%BC%9A))211】。所有 OpenStack 服务统一通过 Keystone 进行身份验证（用户名/密码或token），并使用它的服务目录查找彼此的API地址。运维中经常要与 Keystone 打交道来创建用户、项目(Project/租户)、赋权角色等。

* **Nova（计算服务）**：提供虚拟机 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=))223】。Nova接受用户请求（启动/删除虚拟机等），调度到底层的虚拟化平台（KVM、Xen等）在Compute节点上创建或销毁虚拟机实例。Nova 包含多个子进程：nova-api、nova-scheduler（调度选择宿主机）、nova-conductor、nova-compute（跑在每个计算节点上实际控制 hypervisor）等。

* **Neutron（网络服务）**：管理网络连接，包括创建内部虚拟网络、子网、路由、浮动IP、防火 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=))225】。Neutron让用户能够自助创建隔离的二层网络（类似AWS VPC）、在其上连接虚拟机端口，以及配置对外访问。其后台可集成 Linux Bridge、Open vSwitch 等实现网络虚拟化。Neutron组件包括 neutron-server和各网络代理(agent)进程在网络节点/计算节点上。

* **Cinder（块存储服务）**：提供持久块存储卷（类似云硬盘 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=))227】。用户可创建卷并附加到虚拟机作为额外磁盘使用。Cinder支持各种后端存储驱动（LVM、本地文件、分布式存储或SAN/NAS）。运维需要管理卷类型、容量配额等。

* **Glance（镜像服务）**：提供虚拟机镜像的注 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=))236】。用户可以上传操作系统镜像（比如Ubuntu qcow2文件）到 Glance，然后Nova启动VM时会从Glance取镜像模版。Glance通常存储镜像于文件或对象存储后端。维护上要定期清理老旧镜像，控制仓库大小等。

* **Swift（对象存储）**：提供类似AWS S3的对象 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=%E6%94%B9%E9%95%9C%E5%83%8F%E7%9A%84%E5%85%83%E6%95%B0%E6%8D%AE%EF%BC%9B))236】。它使用分布式架构存储海量非结构化数据，支持多副本和最终一致性。Swift在OpenStack里通常是独立的存储服务，对应大规模存储需求。运维Swift涉及磁盘管理、rebalance等。

* **Horizon（仪表盘）**：OpenStack的Web界面，通过浏览器让管理员和用户操作各服务。Horizon 本身不是后端服务，不管理资源，但它调用各 API 提供友好UI。运维上需要部署Horizon网页服务（Django应用）。

* **RabbitMQ / MQ：** OpenStack内部大量服务间通讯采用消息队列（默认是RabbitMQ）。各组件的controller通过消息RPC与agent通信。RabbitMQ对OpenStack非常关键，需要保证其高可用和性能。

* **数据库：** 大部分 OpenStack 服务使用关系型数据库存储状态信息（MySQL/MariaDB居多）。所以OpenStack的控制节点通常运行一个SQL数据库来支撑各服务的数据存储（租户信息、网络拓扑等）。

* **其他组件：** 还有Heat（编排，类似AWS CloudFormation）、Ceilometer/Aodh（Telemetry/报警）、Tro​ve（数据库即服务）、Magnum（容器即服务，管理K8s集群）等许多项目。核心掌握上述几个即可。

OpenStack 的服务通常以 REST API 形式提供功能。例如 Nova-api 提供计算API, Neutron-api提供网络API。这些API服务进程通常部署在**控制节点**上。**控制节点**一般承载 Keystone、Glance、Nova-scheduler、Neutron-server、Cinder-scheduler等控制服务，以及数据库、消息队列、Horizon等。而**计算节点**主要运行 Nova-compute 和 Neutron L2/L3 agent 等，以管理虚拟机和虚拟网络。**网络节点**可能用于运行 Neutron 的DHCP、L3、LB等代理服务，承载虚拟路由和浮动IP出口。

**典型架构拓扑：**

* 控制节点：运行 Keystone, Glance, Nova-API/Scheduler/Conductor, Neutron-Server, Cinder-API/Scheduler, Horizon, MariaDB, RabbitMQ等。

* 计算节点（可多台）：运行 Nova-Compute (libvirt/KVM), Neutron L2 agent (OVS/bridge) 等，有本地实例存储。

* 网络节点（可和控制合并或独立）：运行 Neutron L3 agent, DHCP agent, Metadata agent 等，连接外部网络提供SNAT/DHCP/metadata等网络功能。

* 存储节点（如果有）：运行 Cinder-volume连相应存储后端，或 Swift object/container/account server等，提供存储资源。

OpenStack 实现高可用通常需要控制节点多副本（3节点架构 etcd+galera+haproxy+rabbit高可用），因为OpenStack本身不自动管理自己的HA，这需要运维以Keepalived/Haproxy等维持API高可用，Galera集群保证数据库HA，RabbitMQ cluster保证消息HA。

总之，OpenStack 是一个庞大的系统，但其核心就是让运维人员能够像云服务商一样管理数据中心：创建虚拟网络、启动虚拟机、配置磁盘和权限等。接下来我们将从运维视角实践OpenStack的基本操作。

### 4.2 部署 OpenStack 实验环境

要深入了解 OpenStack，**实战操作**必不可少。然而全手工部署OpenStack非常复杂，好在有一些工具帮助快速搭建供学习实践的小型环境：

* **DevStack：** OpenStack 官方提供的用于开发和测试的一键部署脚本。DevStack会从源码安装最新版 OpenStack 于一台机器上（All-in-one部署），适合在VM或笔记本上体验OpenStack全套功能。资源需求较高（建议至少8GB内存，4CPU）。

* **Packstack（RDO）：** 在CentOS等系统上可以用 packstack 自动化部署OpenStack（基于RPM包），对新手稍易用，但RDO项目更新略慢。

* **OpenStack Charms / Kolla-Ansible：** 生产就绪的自动部署方案，一个基于juju charms，一个基于容器 ansible部署，但都较复杂，不适合初学了解。

* **MicroStack / MiniShift**：一些简化发行版，如 Ubuntu的 MicroStack snap，可以快速安装一个OpenStack small版；或者 Oracle发布过一个All-In-One appliance 供VirtualBox运行。

* **在线沙箱：** 有些厂商或社区提供OpenStack在线实验环境，可以注册获得几小时试用时段，不用自己安装。

这里我们选择 **DevStack** 方式，它灵活且文档多，适合学习。（提醒：DevStack并非生产部署方案，它安装的服务默认配置简化，安全和性能非最佳，仅供学习实践）。

**DevStack 安装 (All-in-One)：**

1. 准备一台Linux虚机（Ubuntu 20.04或CentOS 8），8GB内存+50GB磁盘以上，连通互联网。

2. 创建一个非 root 用户（如 stack），并给它密码sudo权限。

3. 克隆 devstack 仓库：
      $ git clone https://opendev.org/openstack/devstack.git
      $ cd devstack

4. 创建 `local.conf` 配置文件，至少指定 admin 密码：
      [[local|localrc]]
      ADMIN_PASSWORD=secret
      DATABASE_PASSWORD=$ADMIN_PASSWORD
      RABBIT_PASSWORD=$ADMIN_PASSWORD
      SERVICE_PASSWORD=$ADMIN_PASSWORD

  这个简易配置会设定所有服务密码同 ADMIN_PASSWORD。可以额外设置主机IP,启用服务组件等。

5. 运行安装：
      $ ./stack.sh

  DevStack 脚本会运行约10-30分钟（视网络和机器性能）。期间下载代码、pip安装依赖、初始化数据库等。

6. 成功后，会在终端打印服务列表及 horizon 登录信息。例如：
      This is your host IP: 192.168.1.100
      Horizon is now available at http://192.168.1.100/dashboard
      Keystone is serving at http://192.168.1.100/identity/
      ...

  以浏览器访问 Horizon URL，用户名 "admin"，密码就是 ADMIN_PASSWORD (secret) 即可登录 OpenStack Dashboard。

如果 DevStack 失败，可查看 `stack.sh.log` 查找原因（常见问题：网络不通导致pip超时、或资源不足某服务启动慢失败等）。

**devstack 成功后**，OpenStack各服务就运行在这台虚拟机上。可以通过 Horizon UI试着创建资源，也可以使用 CLI 客户端或者直接访问REST API。

DevStack 已经安装了 OpenStack CLI 工具并做了初始化。source 掉凭据：
    $ source openrc admin admin   # 加载 admin 环境变量
    $ openstack project list      # 列出租户
    $ openstack network list      # 列出网络

`openstack` 命令是统一CLI，后跟子命令管理各种服务资源。DevStack 默认创建了一个admin项目和demo项目，各有admin和demo用户。openrc脚本可切换身份。

### 4.3 OpenStack 基本操作实践

现在我们在 DevStack 环境中以 **管理员** 身份动手实践常用运维操作：

**1. 创建租户(Project)、用户并赋权：**  
OpenStack通常用Project隔离资源，一个项目对应一组资源quota。
    $ openstack project create testproj
    $ openstack user create testuser --project testproj --password Passw0rd
    $ openstack role add --user testuser --project testproj member

这创建了项目'testproj'和普通用户'testuser'，并授予成员角色。此用户可登录Horizon或CLI使用属自己项目的资源。运维人员负责项目与用户管理。

**2. 上传镜像 (Glance)：**  
系统需要有操作系统镜像以供创建虚拟机实例。DevStack默认已下载一个 CirrOS 测试镜像。我们可以上传Ubuntu镜像：
    $ openstack image create "Ubuntu20.04" --file focal-server-cloudimg-amd64.img --disk-format qcow2 --container-format bare --public

将Ubuntu qcow2文件上传为公共镜像，所有用户可见。如果无此文件，可先下载。`openstack image list` 可查看镜像列表。

**3. 创建网络和子网 (Neutron)：**  
OpenStack 分tenant自服务网络和provider外部网络。DevStack默认配置一个外部网络（提供浮动IP）和一个demo用户私网，但我们自己练习：
    $ openstack network create internal-net --project testproj
    $ openstack subnet create internal-subnet --network internal-net --subnet-range 192.168.20.0/24 --gateway 192.168.20.1

（此创建为admin执行的项目网络，或者先`source openrc testuser testproj`用testuser创建，区别在于是private网络归testproj所有）。  
Neutron默认Open vSwitch backend likely configured. The project network is isolated.

**4. 创建路由器以连接项目网络到外部：**  
OpenStack网络模型需要路由器实现私网到外网通信。DevStack默认名为 public 的外部网络。
    $ openstack router create test-router --project testproj
    $ openstack router set test-router --external-gateway public
    $ openstack router add subnet test-router internal-subnet

这样 internal-net 已连上test-router, test-router又连接Public外网。Public网络在DevStack通常NAT到主机网卡，允许出访网络，并提供Floating IP池。

**5. 分配密钥对 (Keypair)：**  
SSH密钥用于登录Linux虚机。创建一对：
    $ openstack keypair create --public-key ~/.ssh/id_rsa.pub testkey

将本地已有公钥导入OpenStack为testproj用户的密钥对'testkey'。这样启动VM时注入公钥，便可用私钥登录VM。

**6. 启动虚拟机实例 (Nova)：**  
准备工作完成，可以创建云主机：
    $ openstack flavor list   # 查看可用flavor(虚机规格), DevStack默认有 m1.tiny etc.
    $ openstack flavor create small --ram 1024 --disk 10 --vcpus 1
    $ openstack server create --flavor small --image "Ubuntu20.04" --nic net-id=$(openstack network show internal-net -f value -c id) --security-group default --key### 4.3 OpenStack 基本操作实践

    在 DevStack 全套环境中，我们以管理员身份完成 OpenStack 的一些基本运维操作，包括创建租户、上传镜像、配置网络及启动虚拟机实例的完整流程。这不仅帮助理解各服务如何协同工作，也为日后真实环境排障打基础。

    **1. 创建项目 (租户) 和用户：** OpenStack 通过 **项目 (Project)** 隔离资源，每个项目类似一个租户账户，拥有各自的虚拟机、网络等资源配额。首先，创建一个新项目供测试使用，并为其创建用户：

    ```bash
    $ source openrc admin admin          # 切换为 admin 环境 (DevStack 会提供 openrc 脚本)
    $ openstack project create testproj
    $ openstack user create testuser --project testproj --password Pa55w0rd
    $ openstack role add --project testproj --user testuser member

上述命令使用 OpenStack CLI 创建了项目 “**testproj**”、用户 “**testuser**”，并授予其在该项目中的 member（成员）角色。此时 `openstack project list` 和 `openstack user list` 可看到新增的项目与用户。**运维意义：** 管理员常需为不同团队或用途创建独立项目和用户，分配资源配额 (quota)，确保不同租户互相隔离。

**2. 上传镜像 (Glance)：** 有了项目，用户才能创建云主机实例。但在此之前需要有操作系统镜像供虚拟机使用。OpenStack 镜像服务 Glance 维护镜像库。DevStack 通常预置了 CirrOS 测试镜像，我们这里上传一个 Ubuntu 镜像作为例：
    $ openstack image create "Ubuntu20.04" \
       --file ubuntu-20.04-server-cloudimg-amd64.img \
       --disk-format qcow2 --container-format bare --public

上面将名为 “Ubuntu20.04” 的镜像注册到 Glance（需提前下载好 qcow2 镜像文件）。`--public` 使其成为公共镜像，可被所有项目使用。如果仅想给特定项目使用，可创建后用 `openstack image set --project testproj <镜像>` 进行共享。通过 `openstack image list` 可查看镜像列表及属性。**运维意义：** 管理员需维护常用操作系统镜像，及时更新安全补丁版本，也要清理过旧或不再使用的镜像节省存储空间。

**3. 创建内部网络和子网 (Neutron)：** 默认情况下，每个项目可以创建自己的私有网络供虚拟机连通。我们切换到 testuser 身份，在 testproj 下创建网络：
    $ source openrc testuser testproj   # 切换到 testproj 用户环境
    $ openstack network create internal-net
    $ openstack subnet create internal-subnet --network internal-net \
        --subnet-range 192.168.20.0/24 --gateway 192.168.20.1

这将创建项目 **internal-net** 私有网络以及一个 192.168.20.0/24 网段的子网。Neutron 会自动运行 DHCP 服务，为该子网的虚拟机分配 IP（第一个可用IP一般为DHCP服务自身）。**运维意义：** 为每个项目准备好网络资源模型，根据需要设置IP段等。如果是管理员创建网络给项目用，可使用 `--project` 参数指定归属。

**4. 配置路由器和外部网络访问：** 虚拟机通常需要访问外部网络或互联网。OpenStack通过 **路由器 (Router)** 将项目私网连接到共享的外部网络上。DevStack 默认有一个名为 “public” 的外部网络，我们将其用作出入口：
    $ openstack router create test-router
    $ openstack router set test-router --external-gateway public
    $ openstack router add subnet test-router internal-subnet

上述操作创建了 **test-router** 路由器，将其上联到外部网络 public，并把先前创建的 internal-subnet 下联到路由器。这样，internal-net 内的虚拟机将通过 test-router 出访外部网络 (SNAT)，也能通过分配浮动IP让外部访问进来。**运维意义：** 通常管理员预先创建好公共网络（绑定实际外部物理网络），项目用户则可自助创建路由器并连接到公共网络，实现与外界通信。排障时，需确保路由器的网关正确配置，并在网络节点运行正常的 L3 转发服务。

**5. 创建密钥对 (KeyPair)：** 为免密登录Linux虚拟机，我们可以注入 SSH 公钥。OpenStack 支持**密钥对**概念，用户可上传公钥，Nova会在虚拟机初始化时将公钥放入 `~/.ssh/authorized_keys`。这里我们假定本地已有 SSH 公私钥：
    $ openstack keypair create --public-key ~/.ssh/id_rsa.pub testkey

这样名为 **testkey** 的密钥对关联到当前用户（testuser）。稍后创建虚拟机时指定 `--key-name testkey` 即可注入该公钥。**运维意义：** 建议用户使用密钥方式登录虚拟机而非默认密码，可提高安全性。管理员可以为用户预置一些通用公钥或者指导其自行添加。另外，也要确保镜像中 cloud-init 等机制启用对接 Nova 对密钥注入（大多数云镜像默认为cloud-init自动做好）。

**6. 启动虚拟机实例 (Nova)：** 准备工作完成，现在可以创建云主机实例（Nova “server”）。我们需要指定**flavor**（虚拟机规格）、镜像、网络、密钥、安全组等参数。DevStack默认有一些flavor，若不存在合适规格可先创建：
    $ openstack flavor list
    $ openstack flavor create m1.small --ram 1024 --disk 10 --vcpus 1

假设我们有了 m1.small 规格，使用之前上传的 Ubuntu 镜像创建一台虚拟机：
    $ openstack security group list   # 查看安全组，默认有 "default"
    $ openstack server create --flavor m1.small --image "Ubuntu20.04" \
        --nic net-id=$(openstack network show internal-net -f value -c id) \
        --security-group default --key-name testkey testVM

这里 `--nic net-id=...` 指定将虚拟机连接到 internal-net 网络（获取其 ID以防名称歧义），`--security-group default` 使用默认安全组（出于简化，DevStack的 default 可能已允许SSH/Ping；如无规则，可后续添加），`--key-name testkey` 注入先前的SSH公钥。**testVM** 是实例名称。执行后 Nova 会安排计算节点来创建该实例。使用 `openstack server list` 可查询到 **testVM** 的状态，当其 `Status` 显示 ACTIVE 时表示启动完成。

接下来给虚拟机分配一个 **浮动IP (Floating IP)** 以便从外部网络访问（DevStack公用网络往往配置为外部，可以提供Floating IP池）：
    $ openstack floating ip create public
    $ openstack server add floating ip testVM <浮动IP地址>

第一条命令从 public 网络的浮动IP池申请一个地址，第二条将该地址关联到实例 testVM。在 DevStack 中，这通常会自动在网络节点配置SNAT/DNAT规则，将外部Floating IP映射到内部实例IP。

现在，我们尝试从控制节点（或能路由到 devstack外网的主机）访问该实例。例如，用 ping 和 SSH：
    $ ping -c 4 <浮动IP地址>
    $ ssh -i ~/.ssh/id_rsa ubuntu@<浮动IP地址>

若安全组规则允许 ICMP 和 SSH，应该可以 ping 通并SSH登录Ubuntu虚拟机（默认云镜像用户名为 “ubuntu”，已通过key注入公钥）。如果无法连接，需检查以下：

* **安全组：** OpenStack默认安全组通常只允许出站所有、入站仅ICMP和SSH。如果规则缺失，可运行：
  
      $ openstack security group rule create --proto icmp default 
      $ openstack security group rule create --proto tcp --dst-port 22 default

  确保ICMP和22端口开放给 default 安全组。

* **网络连通：** 确认 testVM 的内部IP和Floating IP正确映射。用 `openstack server show testVM -f yaml` 查看addresses；在控制节点查看Neutron L3日志看SNAT/DNAT是否创建；确保主机防火墙未阻挡。

* **实例状态：** 若 `openstack server list` 显示实例为 ERROR，则说明调度或启动失败。可能原因包括：镜像损坏、计算节点资源不足等。可用 `openstack console log show testVM` 查看实例控制台输出，寻找错误（如云镜像root磁盘不可读、SSH key注入失败等）。另外 `openstack compute service list` 检查 nova-compute 是否为 Up状态。

* **服务日志：** 如创建时Nova调度失败(No valid host)，应查看控制节点 `/opt/stack/logs/n-sch.log`（Nova调度日志）了解原因，例如无可用内存或CPU；Neutron 网络故障则查看 neutron-* 日志。DevStack日志位于 `/opt/stack/logs/`，生产环境则在 `/var/log/<service>/`。

一切正常的话，我们已成功通过 OpenStack 创建并访问了一台云主机实例。这涵盖了 Keystone 认证 -> Nova 调度创建 -> Glance提供镜像 -> Neutron分配IP网络 -> Cinder（如果挂载卷则涉及）等一 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=,API%E6%9D%A5%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%9E%E4%BE%8B%EF%BC%8C%E5%88%9B%E5%BB%BA%E8%BF%87%E7%A8%8B%E4%B8%AD%E5%8C%85%E6%8B%AC%E5%88%A9%E7%94%A8Nova%E6%9C%8D%E5%8A%A1%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%9E%E4%BE%8B%EF%BC%8C%E8%99%9A%E6%8B%9F%20%E6%9C%BA%E5%AE%9E%E4%BE%8B%E9%87%87%E7%94%A8Glance%E6%8F%90%E4%BE%9B%E9%95%9C%E5%83%8F%E6%9C%8D%E5%8A%A1%EF%BC%8C%E7%84%B6%E5%90%8E%E4%BD%BF%E7%94%A8Neutron%E4%B8%BA%E6%96%B0%E5%BB%BA%E7%9A%84%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%88%86%E9%85%8DIP%E5%9C%B0%E5%9D%80%EF%BC%8C%E5%B9%B6%E5%B0%86%E5%85%B6%E7%BA%B3%E5%85%A5%E8%99%9A%E6%8B%9F%E7%BD%91%E7%BB%9C%E4%B8%AD%EF%BC%8C%E4%B9%8B%E5%90%8E%E5%86%8D%E9%80%9A%E8%BF%87Cinder%E5%88%9B%E5%BB%BA%E7%9A%84%E5%8D%B7%E4%B8%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%8C%82%E8%BD%BD%E5%AD%98%E5%82%A8%E5%9D%97%EF%BC%8C%E6%95%B4%20%E4%B8%AA%E8%BF%87%E7%A8%8B%E9%83%BD%E5%9C%A8Ceilometer%E6%A8%A1%E5%9D%97%E8%B5%84%E6%BA%90%E7%9A%84%E7%9B%91%E6%8E%A7%E4%B8%8B%EF%BC%8CCinder%E4%BA%A7%E7%94%9F%E7%9A%84%E5%8D%B7%EF%BC%88Volume%EF%BC%89%E5%92%8CGlance%E6%8F%90%E4%BE%9B%E7%9A%84%E9%95%9C%E5%83%8F%EF%BC%88Image%EF%BC%89%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87Swift%E7%9A%84%E5%AF%B9%E8%B1%A1%E5%AD%98%E5%82%A8%E8%BF%9B%E8%A1%8C%E4%BF%9D%E5%AD%98%E3%80%82))237】。实践中，还应学会：

* **创建并挂载云硬盘卷：** `openstack volume create` 和 `openstack server add volume` 可动态为实例接入存储，并用 `openstack volume list` 检查状态。

* **使用 Horizon 仪表盘：** 登录 Web UI 图形界面（DevStack 默认 http://<host_ip>/dashboard，admin/密码），通过页面完成网络和实例的创建删除，以熟悉OpenStack的用户体验。

* **资源配额 (Quota)：** 控制各项目最大可用资源数，如 `openstack quota show testproj` 查看，`openstack quota set` 调整。

* **删除/清理资源：** 完成实验后，可执行 `openstack server delete testVM`、`openstack floating ip delete`、`openstack network/router delete` 等清理资源，避免占用。DevStack 提供 `./unstack.sh` 和 `./clean.sh` 来停止服务和清理环境。

### 4.4 运维技巧：日志与故障排除

OpenStack系统由多个组件协同，有时问题可能出现在各种环节。良好的故障排查习惯对运维工程师尤为重要：

* **检查服务状态：** 当某功能异常时，先确认相关 OpenStack 服务是否正常运行。使用 `openstack service list` 可以列出 API 服务注册情况；`openstack compute service list`, `openstack network agent list` 查看各计算节点、网络节点上的后台服务进程是否显示为 “up”。如果某服务 down，可能是该进程宕掉或无法心跳，比如 RabbitMQ 宕机会导致各 agent 无法汇报状态。

* **阅读日志文件：** OpenStack 服务日志信息详细且分散：
  
  * **控制节点日志：** Keystone (`keystone.log`)、Glance (`glance-api.log`)、Nova 控制平面 (如 `n-api.log`, `n-sch.log`, `n-cond.log`)、Neutron Server (`neutron-server.log`)、Cinder 控制 (`c-api.log`, `c-sch.log`) 等。它们记录API请求、调度决策等。出现调用错误 (HTTP 4xx/5xx) 时，可在对应服务日志查到报错原因和堆栈。
  
  * **计算节点日志：** Nova Compute (`nova-compute.log`) 和 Neutron L2 agent (`ovs-agent.log`或`linuxbridge-agent.log`) 等。如果虚拟机无法创建，多半能在 compute 日志看到Libvirt错误或资源不足提示。如实例无法启动控制台或挂载磁盘，可查 compute log 查看与 hypervisor 交互信息。
  
  * **网络节点日志：** Neutron L3 agent (`l3-agent.log`)、DHCP agent (`dhcp-agent.log`)、Metadata agent (`metadata-agent.log`)等。如果浮动IP不通、路由器未创建，l3-agent日志通常会有异常提示。
  
  * **公共组件日志：** RabbitMQ 在 `/var/log/rabbitmq/` 下（如访问延迟会导致RPC超时错误），数据库日志（MySQL一般`/var/log/mysql/`）。如 OpenStack各服务报 RPC timeout，大概率是 RabbitMQ 故障或网络不通。

  **排障示例：** 若用户反馈无法分配浮动IP：检查 Neutron API 日志看请求是否成功；若成功但无法Ping，则登录网络节点检查 linux网桥/iptables 规则；对应查看 l3-agent 日志看是否报错(例如外部网接口缺失)。可能原因包括外部网络配置问题、Neutron L3 agent挂掉等。

* **使用命令诊断：** 善用 OpenStack CLI 和 Linux命令：
  
  * `openstack hypervisor stats show`：汇总计算节点可用资源，判断是否资源耗尽。
  
  * `openstack network agent list`：看网络代理状态，若 L3 agent down，可尝试重启该服务。
  
  * 在控制节点上，使用 `nova-manage` 或 `neutron-debug` 等命令调试。如 `nova-manage service list` 可以类似 CLI 列出服务状态。
  
  * Linux 网络层面，检查计算节点上的虚拟交换机 (br-int, br-ex 等) 接口配置；检查网络namespace：每个路由器、DHCP在网络节点都有独立 namespace，可以 `ip netns list` 找到，进入 `ip netns exec qrouter-xxx ping ...` 测试连通性。

* **重启服务及恢复：** 当某服务进程崩溃或卡死，重启相应服务（DevStack可直接重新 run stack.sh 或 systemctl 重启）。RabbitMQ或数据库宕机需要尽快恢复，恢复后OpenStack服务一般能重连。多节点部署下，可切换到备用节点服务提供，排障采取不影响线上方式进行。

* **故障常见场景：**
  
  * **No valid host**：创建虚拟机时调度无可用宿主机。运维需检查计算节点资源是否耗尽、是不是被设置维护模式 `disabled`、flavor要求的资源/主机 Aggregate 匹配不到节点等。
  
  * **磁盘/卷故障**：如 Cinder 卷无法附加，可能是 cinder-volume 服务未连接存储后端或 Nova 未检测到 iSCSI连接。检查卷状态（error_attaching 等），对应查看 Nova compute 和 cinder-volume 日志。
  
  * **网络性能或错误**：OpenStack虚机间网络慢可能是 overlay封装问题或MTU不当；丢包可能是安全组规则或QoS限制。需从Neutron配置入手调整，如VXLAN隧道MTU设置，或openvswitch流表查看。
  
  * **服务组件故障**：Keystone服务挂掉会导致所有OpenStack API无法认证（提示Unable to authenticate）；Glance挂掉导致新虚机无法获取镜像卡住等。此类情况通常在日志报连接refused或500错误。应及时恢复服务或切换至备份服务。

总之，OpenStack运维排障需要 **宏观定位** (哪个组件/层面的问题) 和 **微观分析** (深入日志和配置)，二者结合。平时应熟悉各组件日志位置和典型报错信息，建立知识库。遇到疑难问题，利用社区资源（官方文档、问 ([[云计算]OpenStack这一篇就够了！ - SkyBiuBiu - 博客园](https://www.cnblogs.com/Skybiubiu/p/16561169.html#:~:text=OpenStack%E6%98%AF%E4%B8%80%E4%B8%AA%E8%87%AA%E7%94%B1%E3%80%81%E5%BC%80%E6%BA%90%E7%9A%84%E4%BA%91%E8%AE%A1%E7%AE%97%E5%B9%B3%E5%8F%B0%E3%80%82%E5%AE%83%E4%B8%BB%E8%A6%81%E4%BD%9C%E4%B8%BA%E5%9F%BA%E7%A1%80%E8%AE%BE%E6%96%BD%E5%8D%B3%E6%9C%8D%E5%8A%A1%EF%BC%88IaaS%EF%BC%89%E9%83%A8%E7%BD%B2%E5%9C%A8%E5%85%AC%E7%94%A8%E4%BA%91%E5%92%8C%E7%A7%81%E6%9C%89%E4%BA%91%E4%B8%AD%EF%BC%8C%E6%8F%90%E4%BE%9B%E8%99%9A%E6%8B%9F%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%92%8C%E5%85%B6%E4%BB%96%E8%B5%84%E6%BA%90%E7%BB%99%E7%94%A8%E6%88%B7%E4%BD%BF%E7%94%A8%E3%80%82%E8%AF%A5%E8%BD%AF%E4%BB%B6%E5%B9%B3%E5%8F%B0%E7%94%B1%E7%9B%B8%E4%BA%92%20%E5%85%B3%E8%81%94%E7%9A%84%E7%BB%84%E4%BB%B6%E7%BB%84%E6%88%90%EF%BC%8C%E6%8E%A7%E5%88%B6%E7%9D%80%E6%95%B4%E4%B8%AA%E6%95%B0%E6%8D%AE%E4%B8%AD%E5%BF%83%E5%86%85%E4%B8%8D%E5%90%8C%E7%9A%84%E5%8E%82%E5%95%86%E7%9A%84%E8%AE%A1%E7%AE%97%E3%80%81%E5%AD%98%E5%82%A8%E5%92%8C%E7%BD%91%E7%BB%9C%E8%B5%84%E6%BA%90%E7%9A%84%E7%A1%AC%E4%BB%B6%E6%B1%A0%E3%80%82%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E5%9F%BA%E4%BA%8E%E7%BD%91%E7%BB%9C%E7%9A%84%E4%BB%AA%E8%A1%A8%E7%9B%98%E3%80%81%E5%91%BD%E4%BB%A4%E8%A1%8C%E5%B7%A5%E5%85%B7%E6%88%96RESTful%E7%BD%91%E7%BB%9C%E6%9C%8D%E5%8A%A1%E6%9D%A5%E7%AE%A1%E7%90%86%E3%80%82))-L4】也是有效手段。

### 4.5 OpenStack 与容器的结合

作为面向虚拟机和基础设施的云平台，OpenStack 也在适应容器化的趋势，并提供了一些与容器集成的途径：

* **Magnum – 容器编排即服务：** Magnum 是 OpenStack 的一个官方项目，用于在 OpenStack 上提供容器编排引 (ChatGPT建议.md)L12】。通过 Magnum，用户可以一键创建由 Kubernetes、Docker Swarm 或 Apache Mesos 驱动的集群（Magnum 将这些称为 COE 集群）。Magnum 内部利用 Heat 编排服务自动创建虚拟机并部署相应的容器编排软件，例如创建若干 Nova 实例并在其上安装配置 Kubernetes Master、Node组件，最后产出一个可用的 K8s 集群。这相当于 OpenStack 充当了容器云的底层，在IaaS上再搭建一层CaaS (Container-as-a-Service)。
  运维人员可通过 Magnum 简化 Kubernetes 集群生命周期管理。例如可以定义K8s集群模板（包含节点flavor规格、网络、镜像等），然后用户通过简单命令 `openstack coe cluster create` 就能得到一个K8s集群。不需要手动为每个团队分配虚拟机搭K8s，Magnum统一管理。Magnum 目前支持 Kubernetes 非常完善，包括与 Keystone 整合认证（支持获取 Keystone token 登录K8s API）。

* **OpenStack 原生容器化部署：** OpenStack 自身也可以运行在容器中。目前生产环境经常使用 Kolla/Kolla-Ansible 或 OpenStack Charms 等工具，将 OpenStack 各组件打包为容器部署。这与用户侧容器无直接关系，但对于运维来说，是掌握容器编排应用的实例。运维OpenStack服务容器化后，更易于升级、隔离依赖。比如 Kolla 使用 Docker 容器运行 Nova、Neutron 等，再用 Ansible 管理容器更新。未来 OpenStack 可能更多以 Kubernetes Operators 方式来管理其控制节点服务。

* **在 OpenStack 上部署 Kubernetes 的其他方式：** 除了 Magnum，很多企业会手工或使用自动化工具在 OpenStack租户上搭建K8s集群。例如：
  
  * **Kubespray：** 一个基于 Ansible 的工具，可以在任意 VM 或裸机上安装 Kubernetes。运维人员先用 OpenStack API创建几台虚拟机，然后用 Kubespray 的剧本将它们配置成 K8s Master 和 Worker 节点。
  
  * **Cluster API Provider OpenStack：** Cluster API 是 Kubernetes社区的集群自管理项目，有OpenStack插件。可以在已有K8s管理集群中，通过声明Cluster对象，自动调用OpenStack API创建所需Nova实例并安装K8s组件。这实现了容器编排与云基础设施的进一步集成。

  通过这些手段，OpenStack 虽然管理的是 VM 等资源，但实际上许多云原生应用的基础设施也可能构建在它之上。因此，OpenStack 运维工程师经常需要和 Kubernetes 运维协作：例如确保底层云网络和安全组支持K8s的负载特性、调整云配额以满足容器集群的动态扩展等。

**OpenStack 与 Kubernetes 优势互补：** OpenStack 提供稳定的 IaaS 能力（计算、存储、网络多租户隔离等），Kubernetes 提供灵活的应用层编排。在私有云环境下，两者可以组合打造企业完整的云平台栈。一方面运维需要精通 OpenStack 来保证底层可靠，另一方面学习 Kubernetes 来支持应用交付。因此，很多云计算工程师需要同时掌握两者，这也是我们设计本学习体系涵盖 OpenStack 和 Kubernetes 的原因。

### 4.6 实践建议与项目经验

完成 OpenStack 基础的学习后，建议通过一些实战项目将所学云原生技术串联起来，不仅巩固知识，也为日后工作积累经验和成果：

* **搭建云原生示例应用环境：** 利用 Linux、Docker、Kubernetes、OpenStack 全栈技术，尝试构建一个完整的示例项目。例如在本地开发一个简单 **微服务应用**（包含前端、后端、数据库），**容器化** 部署在 Docker Compose 上测试，然后**分布式部署**到 Kubernetes 集群运行，最后**迁移**到 OpenStack 私有云上（先在OpenStack上创建几台虚机组成K8s集群，再部署应用）。这个过程中会遇到很多实际问题（网络配置、存储卷、CI/CD部署等），解决这些问题的过程就是宝贵的经验。可以将该项目代码与部署指南整理成文档或发布在 GitHub 上，既巩固知识又对外展示能力。

* **参与开源社区贡献：** 挑选一个感兴趣的云原生开源项目做一些力所能及的贡献。一些起点可以是：
  
  * 给 Kubernetes 的周边工具（如 Helm 图表）或 OpenStack 文档提交修正和改进PR。
  
  * 编写一个简单的 **Kubernetes Operator** 或 **OpenStack API 脚本** 实现自动化任务。
  
  * 参与中文本地化/翻译工作，例如翻译 Kubernetes 或 OpenStack 官方文档，提高对概念的理解同时造福社区。

  开源项目的协作能提升你的 **协作沟通技能**，熟悉团队开发流程，同时也是在真实环境下应用所学技术的最佳途径之一。

* **参加比赛和实习：** 如果在校，可以参加相关的技术比赛（如阿里云天池大赛、腾讯云高校比赛、甚至是一些CTF安全赛涉及DevOps环境部署的），在竞赛压力下快速成长。另外，主动寻求云计算厂商或大型互联网公司的 **实习机会**，在实践中跟随有经验的团队工作，是迅速提升的捷径。实习中要主动学习公司使用的工程方法和工具链，与之前自学的对比，找出不足。

### 第五部分：职业发展与扩展技能

本部分总结云原生运维工程师应具备的综合技能，以及一些行业认可的认证和最佳实践，帮助您在长期职业发展中保持竞争力。

#### 5.1 持续学习与软技能提升

DevOps 和云计算领域技术更新很快，除了掌握具体工具，还要培养一些软技能和持续学习的习惯：

* **沟通与团队协作：** 运维工程师经常需要和开发、测试、安全等团队合作。要练习用清晰简洁的语言描述技术方案、故障原因和解决步骤。在开源社区或公司内部积极沟通反馈也是锻炼协作能力的方式。例如参与 OpenStack 社区邮件列表讨论，或在 Kubernetes Slack 频道提问/答疑。还可以练习编写 Wiki 和技术博客，把复杂问题说明白。良好的沟通协作能够让团队运转更高效，也体现了你的专业素养。

* **英语与文档能力：** 云原生领域大量资料和社区讨论以英语为主。阅读英文文档、提交英文 issue 或回答论坛问题都是常态。建议每天坚持阅读官方博客、Release Note等，积累专业英语词汇。也要重视文档写作，无论是架构设计、运维手册还是故障报告，都需要详细且结构清晰的文档支持。一个习惯是**定期复盘**：每月总结本月学到的知识点或解决的疑难问题，整理成笔记或博客。这不仅加深理解，也在社区建立起个人影响力。

* **认证考试 (Optional)：** 获取业内认证能够在一定程度上证明你的技能掌握程度。目前有几项含金量较高的认证可以考虑：
  
  * **Docker Certified Associate (DCA)：** Docker 官方认证，涵盖容器基础、运行、网络、安全等。
  
  * **Certified Kubernetes Administrator (CKA)** 和 **Certified Kubernetes Application Developer (CKADL83】CNCF 基金会推出的 Kubernetes 认证，前者偏重集群运维管理，后者偏重应用开发部署。考试为实操题，含金量高，拿下其中一个会极大提升你在K8s方面的认可度。
  
  * **OpenStack Certified Administrator (COA)：** OpenStack 基金会提供的管理员认证，验证对OpenStack核心服务的部署和问题处理能力。

  认证不是强制的，但备考过程可以系统梳理知识盲区。如果有余力，拿证书对日后求职简历 (ChatGPT建议.md)L37】。需注意这些认证都有一定有效期，需要持续跟进行业版本更新。

* **DevOps 思维与流程：** 除了工具，更要理解 DevOps 的文化和流程理念。例如敏捷开发、持续集成/持续部署 (CI/CD)、基础设施即代码 (Infrastructure as Code) 等。熟悉业界常用的实践：
  
  * 使用 **Jenkins** 或 **GitLab CI** 搭建 CI/CD 流水线，实现代码提交后自动构建、测试、部署到开发或生产环境。
  
  * 使用 **Git** 做版本控制和合作开发，这是DevOps协作的基石。
  
  * 学习 **基础设施即代码** 工具如 Terraform、Ansible 等，用代码管理和部署底层资源，保证环境配置的一致可重复。
  
  * 了解 **监控与反馈** 机制，例如通过看板工具跟踪开发运维任务状态、通过每次迭代的回顾会议持续改进流程等。这些“工程方法”使得DevOps不仅是技术，更是一种高效工作的方法论。

#### 5.2 云原生运维扩展技能

当你掌握了 Linux/容器/K8s/OpenStack 基础后，可以进一步拓展一些周边技能，以满足企业实际需求并提升自身竞争力：

* **持续交付与自动化部署：** 掌握主流 CI/CD 工具的使用与原理，例如 Jenkins Pipeline 脚本编写，GitLab CI 配置，Github Actions 等。学会将构建、测试、镜像打包、部署步骤串联起来，实现应用的一键部署和回滚。理解 Canary 发布、蓝绿部署等高级发布策略。在基础设施层面，掌握 Terraform 或 CloudFormation 脚本，根据代码快速创建云上资源栈；掌握 Ansible、Chef 等配置管理工具，实现批量配置下发和环境一致性。自动化能力是DevOps工程师的核心竞 (ChatGPT建议.md) (ChatGPT建议.md)L70】。

* **监控、日志与故障定位：** 深入学习监控和日志技术栈。如使用 **Prometheus** 收集 Kubernetes 集群和应用的度量指标，通过 **Grafana** 构建可视化看板和告警规则；部署 **ELK/EFK** 日志系统（Elasticsearch + Logstash/Fluentd + Kibana），集中收集容器日志并提供 (ChatGPT建议.md)L59】。练习针对一个故障告警，从监控指标发现异常、用日志追踪定位根因、最终验证解决的全过程。构建完善的监控告警体系和应急预案，是资深运维的重要职责。

* **公有云平台经验：** 除了自建私有云，熟悉至少一家公有云的运维也是非常有价值的技能。比如学习 AWS 的核心服务（EC2计算、VPC网络、S3存储、RDS数据库、EKS容器服务等），或阿里云的对应产品（ECS云主机、VPC、OSS对象存储、ACK容器 (ChatGPT建议.md)L63】。了解其管理控制台和API/CLI使用。很多企业采用混合云或多云策略，有公有云经验可以帮助你将架构设计得更云优化，并与私有云形成对比。例如熟悉 AWS 的 **IAM** 权限模型，有助于设计 OpenStack Keystone 多租户权限；使用过阿里云的容器服务 ACK，可以借鉴其中网络插件和安全组策略优化自己的 Kubernetes 网络方案。

* **安全与合规：** 云原生环境下安全不容忽视。学习容器和集群的安全最佳实践：
  
  * 对镜像进行安全扫描（使用工具如 Trivy 检查已 (ChatGPT建议.md)L62】；实施镜像签名和可信镜像仓库策略，避免未授权镜像运行。
  
  * Kubernetes 集群启用 **RBAC** 精细访问控制，划分不同团队的权限范围；使用 NetworkPolicy 限制Pod间不必要的网络通信。关注 Kubernetes 最新的安全特性（如 Pod 安全标准PSS取代旧的PodSecurityPolicy）并应用。
  
  * OpenStack 则需确保 API 接口访问受限（开启 TLS、用Keystone Federation或LDAP集成保证认证安全），网络安全组策略合理，后台服务组件（如 RabbitMQ、数据库）做好访问控制和加密。
  
  * 了解常见合规标准（如等保、GDPR）对云平台运维的要求，在搭建监控审计时满足日志留存、操作审计的需要。
  
  * 定期给系统做安全更新和漏洞修补，通过配置管理批量推送关键补丁。

### 第六部分：总结与展望

经过上述循序渐进的学习路线，从 Linux 基础打牢开始，逐步深入 Docker 容器、Kubernetes 编排，最后了解 OpenStack 云平台，我们建立了一套完善的 **云原生运维工程师知识体系**。这套体系不仅关注具体技术点的学习，还强调了实践操作、自动化思维和软技能的培养。

云计算和 DevOps 是一个需要持续实践和终身学习的领域。请牢记以下几点建议：

* **多练习、多提问：** 工程能力来自实践。利用每周15小时的宝贵时间，多在命令行下尝试教程中的例子，也勇于进行拓展实验。遇到问题先独立思考调试，然后善用搜索引擎、官方文档和社区论坛获取帮助。每解决一个问题，你的能力就前进一大步。

* **关注社区动态：** 订阅权威博客（如 Kubernetes Blog、Docker Blog、OpenStack Superuser）、关注GitHub热门项目、收听云原生领域播客。这样可以了解行业最新的发展，如 Kubernetes 发布的新版本功能、Docker 的新工具、OpenStack 社区的方向，以及热门的DevOps工具链演进。保持前瞻性有助于规划下一步学习重点，不会在瞬息万变的技术洪流中掉队。

* **理论联系实际：** 在工作中尝试将学到的新技术应用到现有系统中，哪怕是搭建一个小的CI工具、写一个自动化脚本，都能产生价值。同时，从实际问题出发反过来驱动学习。当线上出现故障时，那就是学习深入某项技术细节的最好时机；当团队提出性能优化目标时，就是你研究调优Linux内核参数、大规模集群架构的强劲动力。

按照本学习体系循序渐进地投入数月时间，并辅以项目实践和社区参与，你将会从零基础跃升为能够独当一面的云原生运维工程师。不仅精通 Linux 操作和脚本、容器编排和自动化、云平台部署和优化，还拥有DevOps所需的大局观和协作能力。这将为你的职业发展打开广阔道路——无论是成为企业内部 DevOps 核心成员，还是云服务提供商的技术专家，亦或自己创业打造高效的研发运维体系，你都已做好扎实的准备。

**祝愿你学有所成，早日成为云原生领域的翘 (ChatGPT建议.md)160】


