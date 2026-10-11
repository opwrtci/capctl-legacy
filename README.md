# CapCtl Legacy (Shell Version Archive)

> ⚠️ **ARCHIVED REPOSITORY / 历史归档仓库**  
> 本仓库为初代基于 Shell/AWK 编写的 `capctl`（全量抓包、Sing-Box 实时日志切片监控与 AI 自动化分流规则挖掘套件）历史代码归档。  
> 现已由纯 Go 编写的高性能自治智能体 **`capctl`**（原 `capctl-agent`）全面替代，并已停止主动维护。

---

## 历史背景

初代 `capctl` 诞生于京东云雅典娜（AX6600, Qualcomm IPQ6018, 3GB RAM, 128GB eMMC）OpenWrt 路由器环境，主要解决了以下核心问题：
1. **轻量抓包与环形切片**：结合 `tcpdump` 循环切片录制，对高通 NSS 硬件加速无损旁路，设置 50% 磁盘防爆红线。
2. **Sing-Box 决策流监控**：基于 FIFO 管道与 AWK 实时提取局域网未命中规则的漏网域名。
3. **AI 辅助研判与分流入库**：调用 Google Gemini API 进行智能判定，并自动同步写入 HomeProxy 分流规则与 GitHub 远端规则库。

## 文件组成

* `capctl`: 初代核心 Shell 运维脚本（包含 4400 余行命令分发与逻辑）。
* `capctl-singbox`: Sing-Box 日志实时提取监控脚本。
* `capctl-rotate`: PCAP 切片轮转后处理脚本。
* `capctl-rotate-singbox`: Sing-Box 日志切片轮转脚本。
* `99-capctl-alert.sh`: 终端 SSH 登录横幅与看门狗状态提示脚本。

## 现代版本

现代纯 Go 版本已重构为统一二进制，具备极速启动（~0.1s）、零 Shell 子进程开销、本地真实探针 0 幻觉底座、类 Pi 交互终端与自主巡检能力。
