# Evoxt 马来西亚 Premium Net (CN2) VPS 性能测评与数据分析

## 测评背景与套餐概述

Evoxt 马来西亚 Premium Net（高级网络）套餐专为优化中国大陆网络连接设计，采用 CN2 优质线路，提供高速稳定的网络体验。官方描述为：“Premium network with upgraded China routes. Only purchase if serving traffic to China. Note: This region has lesser monthly traffic allocation compared to other regions.” 本文将通过详细的测评数据，全面解析这款 VPS 的性能表现，帮助用户了解其实际使用效果。

## 马来西亚 Premium Net 套餐详情

马来西亚 Premium Net 套餐基于 KVM 虚拟化技术，搭载高性能 AMD Ryzen 9 7950x3D 处理器和 NVMe SSD 硬盘，默认配置包括 1 个 IPv4 和 1 个 IPv6。用户可根据需求在后台灵活升级配置，但需注意该区域的流量配额相对较低。以下是本次测评的机器配置亮点：

- **处理器**: AMD Ryzen 9 7950x3D
- **存储**: NVMe SSD，磁盘 IO 性能达 848.9 MB/s
- **网络**: 1Gbps 带宽，500GB 月流量

## 系统性能参数

测评机器的 CPU 为 AMD EPYC-Genoa Processor（实际为 Ryzen 9 7950x3D），搭配 512MB 内存和 5GB SSD 存储。以下为核心参数：

- **磁盘 IO**: 848.9 MB/s，表现出色
- **操作系统**: Debian GNU/Linux 11 (bullseye)
- **内核**: Linux 5.10.0-8-amd64 x86_64

这些参数显示，该 VPS 在基础性能上具备较强的竞争力，适合轻量级应用或对速度要求较高的场景。

👉 [2025年最新Evoxt优惠码和云服务器方案套餐整理汇总](https://bit.ly/evoxt)

## IP 与网络质量测试

### IP 测试结果

- **IPv4 质量**: 测试显示 IP 稳定，未见明显异常。
- **IPv6 质量**: 支持 IPv6，性能表现良好。
- **流媒体解锁**: 未提供具体解锁数据，但网络延迟和速度支持流媒体应用。

### 网络速度测试

#### 三网延迟测试
三网（电信、联通、移动）延迟测试显示，电信 CN2 线路表现最佳，联通和移动因绕路略有延迟。

#### Asia Speedtest.net 测试
以下为亚洲区域的网络速度测试结果：

Location                  Upload       Download     Ping
------------------------------------------------------
Malaysia, Kuala Lumpur    739.47 Mbit/s 617.55 Mbit/s 1.002 ms
Singapore (StarHub)       642.07 Mbit/s 563.00 Mbit/s 7.991 ms
Hong Kong (HGC Global)    331.18 Mbit/s 147.49 Mbit/s 42.012 ms
Japan, Tsukuba            173.54 Mbit/s 71.67 Mbit/s  86.814 ms

#### iperf3 网络测试
IPv4 和 IPv6 的跨区域速度测试如下：

Provider       | Location           | Send Speed    | Recv Speed    | Ping
---------------|--------------------|---------------|---------------|------
Clouvider      | London, UK         | 555 Mbit/s    | 178 Mbit/s    | 164 ms
Leaseweb       | Singapore, SG      | 171 Mbit/s    | 348 Mbit/s    | 177 ms
Clouvider      | Los Angeles, US    | 563 Mbit/s    | 85.2 Mbit/s   | 190 ms

测试表明，马来西亚本地连接速度极高，跨国连接表现稳定。

## 路由与网络路径分析

### 电信路由
- **回程**: 电信 CTG + CN2，经香港回内地，延迟较低。
- **去程**: 通过 CN2 + CTG，经过香港和新加坡，最终到达马来西亚。

### 联通路由
- **回程**: 强制走电信 CTG + CN2，经香港返回。
- **去程**: 联通绕行日本，接驳 NTT 至马来西亚。

### 移动路由
- **回程**: 同样走电信 CTG + CN2，经香港回内地。
- **去程**: 移动 CMI 绕美西，再经日本直连马来西亚。

路由测试显示，电信用户体验最佳，联通和移动因绕路延迟稍高，但整体稳定性良好。

## 性能基准测试

### Geekbench 测试
- **Geekbench 5**:
  - 单核得分：1404
  - 多核得分：1279
- **系统信息**:
  - CPU: AMD EPYC-Genoa（Ryzen 9 7950x3D）
  - 内存: 473 MB
  - 频率: 4.19 GHz

### 磁盘与内存性能
- **内存测试**:
  - 单线程读: 61457.74 MB/s
  - 单线程写: 26316.44 MB/s
- **磁盘 IO (fio 测试)**:
  - 4K 读写: 252.30 MB/s (63.0k IOPS)
  - 1M 读写: 5.27 GB/s (5.1k IOPS)

这些数据表明，该 VPS 的磁盘和内存性能非常强劲，适合高 IO 需求的场景。

## 总结与使用建议

Evoxt 马来西亚 Premium Net VPS 在性能和网络表现上均令人满意。其 CN2 线路优化了与中国大陆的连接，电信用户尤为受益；磁盘 IO 和 CPU 性能强劲，适合运行小型网站、数据库或开发环境。不过，流量配额较少，用户需根据实际需求选择套餐。

- **优点**: 高性能 CPU、NVMe SSD、高速 CN2 网络
- **不足**: 月流量限制较低
- **推荐场景**: 面向中国大陆的轻量级应用、开发测试环境