# Ultra-LSNT 风电预测与控制器侧可行性指导（中文说明）

[English](README.md) · [GitHub 仓库](https://github.com/b1ue13e/Ultra-LSNT)

本公开仓库是论文 *"Controller-side feasibility guidance for wind power forecasting under corrupted SCADA"* 的代码与可复现资产工程，围绕面向 SCADA 异常损坏场景下的风电预测展开。仓库以论文结果复核与脚本复现为目标，而非通用打包软件。

## 核心内容与结构

- **主要任务与模型**：控制器侧在数据异常下的风电预测；模型实现位于 `src/models/`，包括 Ultra-LSNT 与轻量版。
- **公开数据**：标准存放路径为 `data/raw/`（原始 Wind CN）与 `data/processed/`（处理后风电、气象和负荷数据）；根目录保留同名 CSV 仅用于旧脚本向后兼容。
- **评估切分**：`split_manifest_80_20.json` 与 `split_manifest_80_20_unified.json` 给出公开的时序切分索引。
- **结果与图表**：`results/tables/` 与 `results/figures/` 保留论文对应的结果表和配图。

## 快速导航

| 需求 | 文件入口 |
| --- | --- |
| 本地环境配置与快速检查 | [`QUICKSTART.md`](QUICKSTART.md) |
| 数据位置与切分说明 | [`DATA.md`](DATA.md) |
| 训练、鲁棒性、效率和消融脚本 | [`EXPERIMENTS.md`](EXPERIMENTS.md) |
| 代码与目录完整映射 | [`STRUCTURE.md`](STRUCTURE.md) |
| 项目概要 | [`SUMMARY.md`](SUMMARY.md) |
| 历史报告与归档说明 | [`docs/README.md`](docs/README.md) |
| 开源许可与参与说明 | [`LICENSE`](LICENSE)、[`CONTRIBUTING.md`](CONTRIBUTING.md) |

代码依赖列在 [`requirements.txt`](requirements.txt) 中。使用本工程时请遵循公开数据许可与实验指南；本页不承诺未经验证的在线服务或外部算力保证。
