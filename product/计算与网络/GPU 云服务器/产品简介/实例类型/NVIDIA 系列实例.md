## 实例概述
**NVIDIA 系列 GPU 实例 GN?** 不仅适用于深度学习、科学计算等 GPU 通用计算场景，也适用于图形图像处理（3D 渲染，视频编解码）场景；腾讯云以和 **标准云服务器一致的管理方式**，提供快速、稳定、弹性的计算服务。

>**注意：**
>GN? 系列实例用作 3D 图形渲染（GN2 不支持）需要安装 GRID driver 和配置 license server。

## 适用场景
适用于数据吞吐量大且对计算速度有要求的工作场景。
 - 深度学习；
 - 图形图像处理；
 - 视频编解码；
 - 图形数据库；
 - 高性能数据库；
 - 计算流体动力学；
 - 计算金融；
 - 地震分析；
 - 分子建模；
 - 基因组学及其他。

## 硬件规格
基本硬件规格如下图
![](https://main.qcloudimg.com/raw/375f1b8e54a52936f7ca72530d82c84b.png)
#### 规格说明：
- GPU 性能：主要指标为 GPU 的浮点运行能力，TF 代表 T Flops，SP 代表 single-precision 单精度浮点运算，DP 代表 double-precision 双精度浮点运算，INT8 代表 INT8 整数运算，DL 代表 Deap learning Tensor Core 的运算（仅适用 V100）。

- 存储/网络：存储列表展示了当前实例所支持购买的存储类型；网络带宽是指该类型实例所在物理机的网络带宽，某一类型具实例所分配的网络带宽详见购买页。

- 可用区：北二代表北京二区，上一代表上海一区，广三代表上海三区，依此类推。

>**注意：**
>GN2，GN8 提供基于 SSD 的本地存储。采用本地存储时，这些实例的系统盘和数据盘只在实例生命周期内存在；当实例到期或您主动销毁实例时，将擦除其实例存储中的应用程序和数据。我们建议您定期备份或复制您存储在实例存储中的数据。

## 支持范围
- 支持 [包年包月](/doc/product/213/2180#1.-.E5.8C.85.E5.B9.B4.E5.8C.85.E6.9C.88) 和 [按量计费]( /doc/product/213/2180#2.-.E6.8C.89.E9.87.8F.E8.AE.A1.E8.B4.B9) 。
- 支持在基础网络和 [私有网络](/doc/product/213/5227) 中启动。
- 支持 [负载均衡](/doc/product/214/524) 等的业务对接，不增加额外的管理和运维成本，内网流量免费。
