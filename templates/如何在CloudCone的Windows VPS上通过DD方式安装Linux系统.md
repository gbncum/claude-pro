# 如何在CloudCone的Windows VPS上通过DD方式安装Linux系统

本文将详细介绍如何将CloudCone提供的Windows VPS通过DD（Disk Dump）方式转换为Linux系统，包括Debian和CentOS两种主流发行版的安装教程。

## 准备工作

1. 连接Windows远程桌面
2. 下载必要软件：[DD工具下载](https://drive.google.com/file/d/1ZKnBTMWpf38FcvumaSawAdQXRoxSM9V6/view?usp=sharing)

## Debian系统安装步骤

### 第一步：运行DD工具
- 双击运行下载的软件
- 选择英文界面（中文可能出现乱码）
- 完成安装后重启服务器

### 第二步：通过VNC选择启动项
- 在CloudCone后台打开VNC连接
- 在启动界面选择"Debian GNU/Linux - Continue with install process"
- 注意：系统有超时自动选择Windows启动的机制，需及时操作

### 第三步：系统安装配置
1. **网络配置**：
   - 选择英文语言
   - 手动配置网络参数（参数可在CloudCone后台查看）
   - Name server address填写：8.8.8.8
   - Hostname和Domain Name可随意填写

2. **镜像选择**：
   - 镜像源区域选择美国
   - 使用默认镜像下载地址
   - 设置root密码和用户密码

3. **硬盘设置**：
   - 保持默认选项
   - 最后选择"yes"写入硬盘

4. **软件选择**：
   - 取消勾选"Debian desktop environment"和"print server"
   - 勾选"SSH Server"（最小化安装）
   - 如需图形界面可自行选择

5. **GRUB安装**：
   - 保持默认选项
   - 选择将GRUB安装到/dev/vda设备

👉 [【点击查看】2025年最新CloudCone优惠码及特价云服务器方案汇总](https://bit.ly/Cloudcone)

## CentOS系统安装教程

### 准备工作
bash
apt-get install -y xz-utils openssl gawk file

### 下载DD脚本
bash
wget --no-check-certificate https://shell.p1e.cn/reinstall/Network-Reinstall-System-Modify.sh && chmod a+x Network-Reinstall-System-Modify.sh

### 安装CentOS 7
bash
bash Network-Reinstall-System-Modify.sh -CentOS_7

- 默认密码：cxthhhhh.com

### 注意事项
1. DD过程较慢，可能需要半小时以上
2. 安装完成后需手动配置网络：
   - 将dhcp获取改为static
   - 手动输入IP等网络参数

## 系统使用提示
- Debian默认不允许root直接登录
- 可先通过普通用户登录，然后使用`su root`切换
- 如需允许root登录，需修改SSH配置文件

## 性能说明
根据实测，通过DD方式安装的Linux系统在CloudCone VPS上运行稳定，网络性能良好，适合各类建站和应用部署需求。