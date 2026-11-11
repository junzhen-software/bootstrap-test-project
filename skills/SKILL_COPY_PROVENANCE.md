# Skill v1.0.1 指定版本随附副本 — 来源与校验

本目录 `skills/AI_PROJECT_BOOTSTRAP/` 是指定版本随附副本，按任务书 §6.1
「测试材料投递通道」第 2 项制作：由固定 Tag 对应内容制作，公开可读，
供被测 AI 获取 Skill 依赖材料。

> 声明：原 Release、原 Tag、原 Commit 均未被修改，Tag 仍指向其原始 commit。
> 本副本在复制基础上执行了材料完整性整改（见第 3 节），
> 因此与 Tag 内 blob 并非逐字节等同，逐文件哈希以下表（本副本实算）为准。

## 1. 来源

| 项目 | 值 |
|---|---|
| 来源仓库 | `example-org/software-project-governance` |
| 来源 Tag | `v1.0.1`（annotated tag `7bc98eb4933a6d5c67d0cd852d1d9dd14fdeaa1f`） |
| 目标 Commit | `c0942b2752ebcbccd648e9f754300a8f6c27be56` |
| Tag 时间 | 2026-11-10T06:06:44Z |
| 复制方式 | GitHub Git Blobs API 按 blob SHA 原样取字节，不做换行规范化 |
| 文件数 | 19 |

## 2. 逐文件清单与 SHA-256（本副本实算）

| 相对路径（位于 `skills/` 下） | 字节 | SHA-256 |
|---|---|---|
| `AI_PROJECT_BOOTSTRAP/INITIALIZATION.md` | 467 | `3b6a4235c5cf60a5dd8d9a160d9f697f696ff4a1d396490c2a9c91fe4341d789` |
| `AI_PROJECT_BOOTSTRAP/LICENSE` | 1081 | `55402782389f201f74eca0d8f180c0860665e0292162a0f1914f8080d999383a` |
| `AI_PROJECT_BOOTSTRAP/PORTABLE_QUICKSTART.md` | 4791 | `cabc5793575368518b5cb9cb2f34a571d0f5211f8cac70f156f434116c9e060d` |
| `AI_PROJECT_BOOTSTRAP/README.md` | 2396 | `8013320bb2dc147a2fdc6156a2d1a960c9961cd6489aaa403274864c6cbb281e` |
| `AI_PROJECT_BOOTSTRAP/SKILL.md` | 17927 | `45c4fd399eb4933693761e22002c5a12174c13bcb9c86bfb068ac838ec2e0d6b` |
| `AI_PROJECT_BOOTSTRAP/SKILL_CHANGELOG.md` | 1385 | `fb499198a3bf6d136ce8a4b99099cac789e232fa5c2f7707003235019d13dd78` |
| `AI_PROJECT_BOOTSTRAP/SKILL_DECISION_LOG.md` | 5874 | `da099d173f8313ec4b5ddc3aef8ed44952adff55e5c0e26dd77634ce2740fb11` |
| `AI_PROJECT_BOOTSTRAP/SOURCE_PROVENANCE.md` | 3694 | `ec0257b2d2d41be6b57d10a4f56f2d09034c687c4df9801e5e5804025d44db4b` |
| `AI_PROJECT_BOOTSTRAP/examples/PROJECT_STRUCTURE.md` | 1222 | `2c3703084ae58f2591521ec8ecaad966732ca6977a54bee5844e8c60f4ea523a` |
| `AI_PROJECT_BOOTSTRAP/references/EXECUTION_PLAYBOOK.md` | 3403 | `740e620a31004a1ca664fa11c1bafb97492908984e1a22df148e065cbe4d5085` |
| `AI_PROJECT_BOOTSTRAP/references/GOVERNANCE_MODEL.md` | 4008 | `680e717c69540a272b173d8239975b62119f2de81c91c0d48281fb848e7c903a` |
| `AI_PROJECT_BOOTSTRAP/references/PROJECT_BOOTSTRAP_CHECKLIST.md` | 3479 | `7952b3f5c7a006ea27cf80ede938235beb400584728ddd9886e42e1ac32da277` |
| `AI_PROJECT_BOOTSTRAP/references/RECOVERY_AND_COLDSTART.md` | 3572 | `59045dceab91ca4227a64d72bf010ce15e918a62cbe80f80a6ccc7cb040ddcdc` |
| `AI_PROJECT_BOOTSTRAP/templates/ACCEPTANCE_TEMPLATE.md` | 1197 | `b6de405240ac3cfe4fa735b0cdcdef95ada2f5fbe2ad982f107a980655e8657e` |
| `AI_PROJECT_BOOTSTRAP/templates/DECISION_RECORD_TEMPLATE.md` | 534 | `fd7b61479649218abf5029432f4355237f3027b06f619c916288d49047b2bd9b` |
| `AI_PROJECT_BOOTSTRAP/templates/EXECUTION_RECORD_TEMPLATE.md` | 946 | `de7e3f708c460208f3b282e5bce4d93d403c00c70734211888f7815289164e28` |
| `AI_PROJECT_BOOTSTRAP/templates/HANDOFF_TEMPLATE.md` | 602 | `3278479d7f4eebf037fde764232c72ee6cd021e61dec4195595329c21db363bb` |
| `AI_PROJECT_BOOTSTRAP/templates/INCIDENT_TEMPLATE.md` | 1069 | `6415857f96a0c83c9391db0ca5fd6076281dcfd209712f58ad4dfb29c09abd15` |
| `AI_PROJECT_BOOTSTRAP/templates/TASK_TEMPLATE.md` | 1323 | `7380fbc01673558d64703c5e75e17aa03ef24cb722487583d7ee29e1e4f12fa2` |

## 3. 与本副本来源 Tag 的差异（完整性整改）

| 类型 | 对象 | 说明 |
|---|---|---|
| 重命名 | `DECISION_LOG.md` → `SKILL_DECISION_LOG.md` | 与项目侧 `docs/DECISION_LOG.md` 存在同编号异义（DEC-003、DEC-004），改名以消除歧义；内容未删改 |
| 重命名 | `CHANGELOG.md` → `SKILL_CHANGELOG.md` | 避免与项目级变更记录位置混淆；内容未删改 |
| 引用同步 | `README.md` 1 处、`SOURCE_PROVENANCE.md` 3 处 | 仅更新指向上述两个文件的名，未改其他表述 |
| 来源标识替换 | `SKILL_DECISION_LOG.md` 3 处、`SOURCE_PROVENANCE.md` 3 处、本文件 1 处 | 真实组织名与私有仓库链接替换为 `example.com` / `example-org` 占位符；Tag 与 Commit 标识保持不变 |

除上述条目外，`SKILL.md`、`references/`、`templates/`、`examples/`、`LICENSE`、
`INITIALIZATION.md`、`PORTABLE_QUICKSTART.md` 内容与来源 Tag 一致。

## 4. 校验方法

```
cd skills/AI_PROJECT_BOOTSTRAP
find . -type f | sort | xargs sha256sum
```

逐行与第 2 节比对。任何一行不一致，即表示副本被改动，不得用于投递。
校验时不要使用会转换换行符的工具（`core.autocrlf=true` 的 git 工作树）；
副本以 LF 换行存储。
