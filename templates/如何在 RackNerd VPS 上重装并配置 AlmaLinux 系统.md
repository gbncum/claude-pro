# 如何在 RackNerd VPS 上重装并配置 AlmaLinux 系统

## 系统重装指南

RackNerd VPS 提供多种 Linux 发行版选择，包括：

- AlmaLinux
- CentOS
- Debian
- Fedora
- Rocky Linux
- Ubuntu

### 为什么选择 AlmaLinux？

在选择系统时，AlmaLinux 因其出色的稳定性和与 CentOS 的兼容性而备受推荐。与 Debian 相比，AlmaLinux 更适合追求企业级稳定性的用户。

> 专业建议：如果您更注重稳定性、与 CentOS 的兼容性和不断增长的社区支持，AlmaLinux 是理想选择。若您更看重软件新颖性和更广泛的软件包选择，Debian 可能更适合。

### 重装步骤

1. 在控制面板选择 AlmaLinux 8 或 9 版本
2. 点击 **Reinstall** 按钮开始重装
3. 重装完成后，需清除本地 SSH 已知主机记录：
   bash
   vi ~/.ssh/known_hosts
   
   删除对应 VPS IP 的记录

👉 [【点击查看】2025年最新 Racknerd 优惠码及特价云服务器方案汇总](https://bit.ly/Rack_Nerd)

## 系统初始化配置

### 基础设置

#### 修改主机名
bash
hostnamectl set-hostname my_host_name

#### 安全加固
1. 禁用 ICMP 响应（防 ping）：
   bash
   echo "net.ipv4.icmp_echo_ignore_all = 1" >> /etc/sysctl.conf
   sysctl -p
   

2. 关闭 SELinux：
   bash
   setenforce 0
   sed -i "s/SELINUX=enforcing/SELINUX=disabled/g" /etc/selinux/config
   

### SSH 安全配置

#### 修改默认端口
1. 检查端口可用性：
   bash
   yum -y install lsof
   lsof -i:1234
   

2. 防火墙放行新端口：
   bash
   firewall-cmd --add-port=2222/tcp --permanent
   firewall-cmd --reload
   

3. 修改 SSH 配置：
   bash
   vi /etc/ssh/sshd_config
   
   将 `#Port 22` 改为 `Port 1234`

4. 重启服务：
   bash
   systemctl restart sshd
   

#### 用户管理
1. 创建新用户：
   bash
   adduser username
   passwd username
   

2. 赋予管理员权限：
   bash
   usermod -aG wheel username
   

3. 禁用 root 远程登录：
   修改 `/etc/ssh/sshd_config` 中 `PermitRootLogin` 为 `no`

## 性能优化

### 启用 BBR 加速
RackNerd VPS 通常默认已开启 TCP BBR 拥塞控制算法，可显著提升网络性能。

### 配置 SSH 密钥登录
bash
ssh-copy-id -p 1234 username@server-ip

## 常用工具安装

### 基础软件包
bash
sudo dnf clean all
sudo dnf update
sudo dnf groupinstall "Development Tools"
sudo yum -y install wget git zsh tar util-linux-user lua

### 特色工具
1. Tailscale VPN：
   bash
   curl -fsSL https://tailscale.com/install.sh | sh
   

2. 模糊查找工具 fzf：
   bash
   sudo dnf install epel-release
   sudo dnf install fzf
   

3. Neovim 编辑器：
   通过 EPEL 仓库安装最新版本

## 终端环境配置

### Zsh 优化
1. 修改默认终端：
   bash
   sudo chsh -s /bin/zsh
   

2. 增强功能：
   在 `~/.zshrc` 中添加：
   bash
   export TERM=xterm-256color
   plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
   bindkey ',' autosuggest-accept
   

### Powerlevel10k 主题
1. 安装：
   bash
   git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
   

2. 配置：
   修改 `~/.zshrc` 中的 `ZSH_THEME` 为 `powerlevel10k/powerlevel10k`

通过以上步骤，您可以在 RackNerd VPS 上快速部署一个安全、高效的 AlmaLinux 服务器环境。