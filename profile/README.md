# biorchestra

**Agent-as-a-Service bioinformatics platform** · Agent 编排的生信工具云服务

面向研究者的分子性质预测、毒性评估、靶点预测、分子对接与富集分析，
由云侧 agent（Go + Eino）统一编排，浏览器即全部入口。

| 仓库 | 角色 |
|---|---|
| [`platform`](../platform) | 主仓：Go 单体（Hertz + Eino + River）+ Web 前端 + API/工具契约真源 + ADR |
| [`tool-python`](../tool-python) | 常驻模型服务：分子性质 / VenomPred 毒性 / DrugCLIP 靶点 / NP 分类 |
| [`tool-r-analytics`](../tool-r-analytics) | 常驻 R 分析服务：富集分析 / PPI / 绘图 |
| [`tool-docking`](../tool-docking) | 一次性 Job 容器：Vina 对接 pipeline（job 信封契约） |
| [`models`](../models) | 权重清单真源（sha256 / uri / license）；权重本体不进 git，走 Release/对象存储 |
| [`deploy`](../deploy) | GitOps 部署真源（kustomize + SOPS + self-hosted runner） |
| `.github` | 本仓：org 级 reusable workflows 与组织约定 |

## 工程约定

- 分支模型 trunk-based：`main` + 短命分支，**squash-only**，conventional commits
- 各仓独立 semver tag；容器镜像统一发布到 `ghcr.io/biorchestra/<repo>`
- 权重治理：`models` 仓 manifest 为唯一真源，上载与校验走
  `import_local.py → formalize.py → backfill_uri.py → verify.py` 闭环
- 密钥管理：SOPS + age 加密进 `deploy` 仓；CI 与 runner 上不落多余秘密

## 状态

邀请制 beta 筹备中 · 全部仓库私有
