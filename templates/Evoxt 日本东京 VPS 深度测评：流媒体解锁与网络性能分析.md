# Evoxt 日本东京 VPS 深度测评：流媒体解锁与网络性能分析

## 测试IP与Looking Glass信息
- **测试IP**: 23.27.52.101（日本东京数据中心）
- **Looking Glass**: 可通过该IP测试网络路由和延迟

## 流媒体解锁能力实测
plaintext
 ** IPv4 解锁测试结果
--------------------------------
 ** 服务商: Evoxt Enterprise (23.27.*.*)

============[ 跨国流媒体 ]============
 Dazn:                          ✔️ 日本区
 Disney+:                       ✔️ 日本区
 Netflix:                       ✔️ 日本区
 YouTube Premium:               ✔️ 日本区
 Amazon Prime Video:            ✔️ 日本区
 TVBAnywhere+:                  ✔️
 Spotify:                       ✔️ 日本区
 ChatGPT:                       ✔️
 Google Gemini:                 ✔️ 日本区
=======================================

 ** IPv6 解锁测试结果
--------------------------------
Netflix/YouTube仍可解锁日本区，但部分服务如Dazn/Disney+暂不支持IPv6

## 网络路由测试（TCP回程）
### 中国电信线路
plaintext
1   10.1.1.21       *                         内网地址          
2   93.118.40.18    AS58325                   多伦多节点  
3   63.222.112.186  AS3491                    南非节点  
4   63.216.142.10   AS3491                    香港PCCW节点 (47.46ms)
5   203.22.178.214  *                         上海CTGNet节点 (76.81ms)
6   59.43.22.5      *                         中国电信CN2骨干网 (81.51ms)

### 中国移动线路
plaintext
4   63.223.17.90    AS3491                    香港PCCW节点 (47.82ms)
7   223.120.2.117   AS58453                   香港移动CMI节点 (83.66ms)
8   221.183.92.193  AS9808                    广州移动节点 (172.16ms)

👉 [【点击查看】2025年最新 Evoxt优惠码及特价云服务器方案汇总](https://bit.ly/evoxt)

## 网络性能基准测试
| 节点        | 上传速度   | 下载速度    | 延迟   |
|-------------|------------|-------------|--------|
| 东京本地    | 1455 Mbps  | 553 Mbps    | 27ms   |
| 新加坡      | 939 Mbps   | 3754 Mbps   | 72ms   |
| 中国电信    | 689 Mbps   | 788 Mbps    | 97ms   |

## 服务器硬件性能
plaintext
 CPU: AMD EPYC-Genoa (1核 @3.69GHz)
 内存: 457MB DDR4
 存储: 4.9GB NVMe (平均IO速度1536MB/s)
 虚拟化: KVM with AES-NI加速
 位置: 日本东京（AS149440）

## 使用建议
1. **适合场景**：
   - 日本区流媒体解锁
   - 东亚地区低延迟业务
   - 需要IPv4/IPv6双栈的服务

2. **网络优化**：
   - 中国电信用户推荐走CN2线路
   - 移动用户直连香港CMI节点

3. **性能提示**：
   - 建议搭配BBR加速算法
   - 高IO性能适合数据库应用

> 测试数据来自第三方评测，实际体验可能因网络环境而异