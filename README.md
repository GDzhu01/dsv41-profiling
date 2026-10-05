# DSV4.1 Ascend Profiling

原始 profiling 存放在 **[Releases 下载页](https://github.com/GDzhu01/dsv41-profiling/releases/tag/d0-dp0-running50-20261005)**，不是首页代码目录。

## 下载原始 profiling

- **[下载完整原始 profiling（约 63 MB）](https://github.com/GDzhu01/dsv41-profiling/releases/download/d0-dp0-running50-20261005/d0-dp0-running50-raw.tar.gz)**
- [SHA256 校验文件](https://github.com/GDzhu01/dsv41-profiling/releases/download/d0-dp0-running50-20261005/SHA256SUMS)

这是私有仓库，下载需要登录有权限的 GitHub 账号。

## 采集信息

| 项目 | 配置 |
| --- | --- |
| 时间 | 2026-10-05 17:16，UTC+8 |
| 模型 | DeepSeek-V4.1-Flash |
| 目标 | D0 / DP0，单 NPU / TP1 |
| 负载 | 1600 并发、1600 请求，输出 4096 tokens |
| Proxy | 4 workers |
| Prefix cache | repeat_rate=100%，所有 P DP 已预热 |
| 采集窗口 | Running=50 时触发，约 2 秒 |
| 窗口内采样 | 18 次均为 Running=50、Waiting=0 |
| 请求结果 | 1600 成功、0 失败 |

## 压缩包内容

完整 `*_ascend_pt/` 目录，包含原始采集数据和已解析数据：

- `ASCEND_PROFILER_OUTPUT/trace_view.json`：设备时间轴。
- `ASCEND_PROFILER_OUTPUT/kernel_details.csv`：74,590 条设备事件。
- `ASCEND_PROFILER_OUTPUT/operator_details.csv` 等解析文件。

设备事件跨度约 2.093 秒。Profiling 会扰动运行，本轮不作为无 profiler 的性能基线。

```bash
sha256sum -c SHA256SUMS
tar -xzf d0-dp0-running50-raw.tar.gz
```

SHA256：`abc5aecd0b96248b1a02a5b4749edec7b64ad25a5ca2db420a179824aed0973e`
