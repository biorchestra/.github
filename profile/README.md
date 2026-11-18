# biorchestra

Agent 编排的生信工具云服务（私有组织——仓库与代码全部私有）。

| 仓库 | 角色 |
|---|---|
| `platform` | 主仓：Go 单体（Hertz+Eino+River）+ Web 前端 + 契约真源 + ADR |
| `tool-python` | 常驻模型服务：RDKit 性质 / VenomPred 毒性 / DrugCLIP 靶点 / NP 分类 |
| `tool-r-analytics` | 常驻 R 分析服务：clusterProfiler 富集 / PPI / 绘图 |
| `tool-docking` | 一次性 Job 容器：Vina 对接 pipeline（5 阶段，job 信封契约） |
| `models` | 权重清单真源（sha256/uri/license）；权重本体不进 git |
| `deploy` | GitOps 部署真源（kustomize + SOPS+age + self-hosted runner） |
| `.github` | 本仓：org 级 reusable workflows 与约定 |

约定：trunk-based · squash-only · conventional commits · 各仓独立 semver · 镜像 `ghcr.io/biorchestra/<repo>`。
