# DSV4.1 Ascend Profiling

原始 profiling 和解析报告存放在 GitHub Releases。仓库为公开仓库。

## 最新：Engram overlap，384 并发，D0/DP0 running=12（2026-10-06）

[打开 Release](https://github.com/GDzhu01/dsv41-profiling/releases/tag/engram-overlap-c384-dp0-running12-20261006)

- [原始 profiling](https://github.com/GDzhu01/dsv41-profiling/releases/download/engram-overlap-c384-dp0-running12-20261006/engram-overlap-c384-dp0-running12-20261006-raw.tar.gz)
- [解析报告 HTML / XLSX / Markdown、每 DP 性能数据及采集证据](https://github.com/GDzhu01/dsv41-profiling/releases/download/engram-overlap-c384-dp0-running12-20261006/engram-overlap-c384-dp0-running12-20261006-analysis.tar.gz)
- [SHA256SUMS](https://github.com/GDzhu01/dsv41-profiling/releases/download/engram-overlap-c384-dp0-running12-20261006/SHA256SUMS)

384 并发、384 请求全部成功；输出 4096 tokens，repeat_rate=100%，P 全部 DP 已预热。Engram overlap 开启，DSpark 入图，Static / Super Kernel 关闭。

DP0 running=12、waiting=0 时采集 **2.003 秒**，窗口内 19 次采样均保持此并发。解析出 **171,719 个设备事件、88 个完整 step**，step P50 **23.131 ms**、P90 **23.165 ms**。

本轮 TPOT **6.1 ms**，整体输出吞吐 **49,981.41 tokens/s**，D 各 DP 打屏峰值 **2161.6–2168.3 tokens/s**。本轮包含 profiling 开销。解压分析包后打开 `analysis/report/report.html`。

## 历史：PR11 dSpark + skip-allreduce，D0/DP0 running=50，v2

[打开 v2 Release](https://github.com/GDzhu01/dsv41-profiling/releases/tag/pr11-dspark-skipallreduce-dp0-running50-v2-20261005)

- [原始 profiling](https://github.com/GDzhu01/dsv41-profiling/releases/download/pr11-dspark-skipallreduce-dp0-running50-v2-20261005/pr11-dspark-skipallreduce-d0-dp0-running50-v2-raw.tar.gz)，SHA256 `9e974b7ee49f12f1c34551ec30949b6559d499fce1bc0318ddc874ddef1fba3c`
- [解析报告](https://github.com/GDzhu01/dsv41-profiling/releases/download/pr11-dspark-skipallreduce-dp0-running50-v2-20261005/pr11-dspark-skipallreduce-d0-dp0-running50-v2-analysis.tar.gz)，SHA256 `2acaa7ad32e47bfa9cc2df4d86f4efbbe51897bb7450ce594b36b9b1103c6af9`
- [SHA256SUMS](https://github.com/GDzhu01/dsv41-profiling/releases/download/pr11-dspark-skipallreduce-dp0-running50-v2-20261005/SHA256SUMS)

| 项目 | 配置 |
| --- | --- |
| 时间 | 2026-10-05 19:23，UTC+8 |
| 代码 | `cca6200f2ed01f2e9420485a0b593c02eb7d9de6` |
| 模型 | DeepSeek-V4.1-Flash |
| 模式 | MRV2、dSpark FULL graph、skip DP coordination |
| 目标 | D0 / DP0，单 NPU / TP1 |
| 负载 | 1600 并发、1600 请求、129054 输入、4096 输出 |
| Prefix cache | repeat_rate=100%，16 个 P DP 均完成预热 |
| 采集窗口 | Running=50、Waiting=0 时触发，目标窗口约 2 秒 |
| 窗口验证 | 28 次采样均为 Running=50、Waiting=0 |
| 请求结果 | 1600 成功、0 失败 |
| 原始事件 | 78,754 条，40 个完整 decode step |

解析报告压缩包包含 `report.html`、`report.xlsx`、`report.md`、诊断结果及 evidence 索引。原始压缩包包含完整 `*_ascend_pt/` 目录和 `ASCEND_PROFILER_OUTPUT/`。

## 历史：D0/DP0 running=50，v1

[打开 v1 Release](https://github.com/GDzhu01/dsv41-profiling/releases/tag/d0-dp0-running50-20261005)

- [原始 profiling](https://github.com/GDzhu01/dsv41-profiling/releases/download/d0-dp0-running50-20261005/d0-dp0-running50-raw.tar.gz)
- SHA256 `abc5aecd0b96248b1a02a5b4749edec7b64ad25a5ca2db420a179824aed0973e`

```bash
sha256sum -c SHA256SUMS
```
