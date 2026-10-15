# 王瑛琦

嵌入式软件 / C++ · ROS2 机器人系统 · 传感器驱动

南京航空航天大学 航空学院 · 飞行器设计与工程（控制与嵌入式方向）· 2027 届

**求职方向：嵌入式软件 / C++ 软件开发（2027 届校招）**

---

## 关注方向

嵌入式与机器人软件：设备驱动、通信协议解析、实时控制回路，
以及在资源受限平台上让这些东西稳定跑起来。

主用 C++，熟悉 Linux / POSIX 环境下的开发与调试。

## 项目

### [unilidar-driver](https://github.com/qi-neo/unilidar-driver) — 宇树 L1 激光雷达 ROS2 驱动

自行实现 UDP 报文解析与几何换算，发布标准 `PointCloud2` 与 `Imu` 话题，
不依赖官方预编译静态库，可作为官方节点的 drop-in 替换。

- 报文定界只用「帧尾标识 + CRC32」，不硬编码整包长度
  （官方协议头文件的字节数注释与自身字段不一致，照抄会整批判坏）
- 传输 / 协议 / 解码三层不依赖 ROS，可在无 ROS 环境编译并跑断言
- 63 项离线自检 + 变异测试 + 实测定界探针；CI 覆盖双编译器与 ASan/UBSan
- 附[驱动编写方法论文档](https://github.com/qi-neo/unilidar-driver/blob/main/docs/driver-design.md)

`C++17 · ROS2 · UDP · CRC32 · CI`

### [active-suspension-lidar-preview](https://github.com/qi-neo/active-suspension-lidar-preview) — 激光雷达预瞄主动悬架

国家级大学生创新训练计划项目（主持）。用激光雷达随车速自适应预瞄路面高程
（0.5–5 m），融合 IMU 姿态反馈，驱动四轮独立作动器抑制车身振动。实车 A/B
测试中车身横滚与俯仰角波动各降低约 81%。

- 控制器核心不依赖 ROS 与 PCL，可脱离整车编译自检（142 项检查）
- 安全状态机：零位标定 → 找平 → 闭环，含降级与急停两条异常分支
- 无导数 PD / 增量式 LQI 双控制律 + 车速自适应预瞄前馈 + 帧龄运动补偿
  + 前后轴差异化取样 + 运动学解耦
- 五个 ROS2 包在 CI（ROS Humble 容器）中完整构建并跑通全部离线自检

`ROS2 · C++ · PCL · 嵌入式 · 多传感器融合`

### [maixcam-esp32-tcp-stepper-motor](https://github.com/qi-neo/maixcam-esp32-tcp-stepper-motor)

MaixCAM Pro 与 ESP32 通过 socket TCP 通信控制步进电机的完整实现，
含两端代码与通信协议设计。

`C++ · 嵌入式 · TCP · 步进电机`

## 技术栈

| 类别 | 内容 |
|---|---|
| 语言 | C++（主）、Python |
| 系统 / 平台 | Linux / POSIX、ROS2（Humble / Jazzy）、香橙派 AI Pro、昇腾 Atlas 310 / 310B |
| 通信协议 | UDP / 串口（termios、CRC16 / CRC32 帧协议）、TCP |
| 机器人 | 传感器驱动、通信协议解析、实时控制回路 |
| 库与工具 | PCL、Eigen、CMake、Git、GitHub Actions、ASan / UBSan |
| 工程实践 | 分层架构、离线自检、变异测试、持续集成、开源许可证合规 |

## 竞赛获奖

周培源大学生力学竞赛（全国奖、省级二等奖）· 数学建模竞赛 · 创新竞赛

## 联系方式

- GitHub：[@qi-neo](https://github.com/qi-neo)
- 邮箱：qi-neo@users.noreply.github.com
