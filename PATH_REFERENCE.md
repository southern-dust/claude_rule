# .claude 目录路径参考

本文档提供 `.claude` 目录内所有文件的完整路径参考，使用基于项目根目录的逻辑路径格式。

## 路径表示约定

**约定**: 本文档中所有路径使用 `$PROJECT_ROOT` 表示项目根目录

```bash
$PROJECT_ROOT = 项目根目录（逻辑表示）
# 示例：/path/to/your/project
```

**说明**: `$PROJECT_ROOT` 是逻辑路径表示，用于指代项目根目录的位置，便于文档在不同环境中保持一致性。

---

## 目录概览

```
$PROJECT_ROOT/.claude/
├── 核心项目文档 (10个文件)
├── coding-prompt/        # Git子模块：外部LLM开发标准
├── docs/                 # 项目文档 (4个文件)
├── doc-template/         # 可复用文档模板 (13个文件)
├── project-guideline/    # 开发规范与工作流 (4个文件)
└── scripts/              # 实用工具脚本
```

**统计**: 9个目录，36个文件，1个Git子模块

---

## 分类路径映射

### Category A: 核心项目文档 (Root Level)

| 路径 | 用途 | 读者 | 更新频率 |
|------|------|------|----------|
| `$PROJECT_ROOT/.claude/claude_guide.md` | Claude AI使用指引 | Claude AI | 文档结构调整时 |
| `$PROJECT_ROOT/.claude/README.md` | 项目说明文档 | 开发者 | 项目变更时 |
| `$PROJECT_ROOT/.claude/project_state.md` | 项目当前状态 | Claude AI、开发者 | 功能完成/状态变更 |
| `$PROJECT_ROOT/.claude/design_spec.md` | 技术架构规范 | Claude AI、架构师 | 架构变更/接口调整 |
| `$PROJECT_ROOT/.claude/development_plan.md` | 开发路线图 | Claude AI、项目经理 | Phase完成/计划调整 |
| `$PROJECT_ROOT/.claude/requirements.md` | 产品需求文档 | Claude AI、产品经理 | 需求变更时 |
| `$PROJECT_ROOT/.claude/TODO.md` | 任务跟踪列表 | Claude AI、开发者 | 任务完成/需求新增 |
| `$PROJECT_ROOT/.claude/MIGRATION_SUMMARY.md` | 迁移历史记录 | 开发者 | 迁移操作后 |
| `$PROJECT_ROOT/.claude/settings.local.json` | 本地配置 | 系统 | 配置变更时 |
| `$PROJECT_ROOT/.claude/.gitmodules` | Git子模块配置 | Git | 子模块变更时 |

### Category B: 外部标准 (Git Submodule)

**子模块**: `coding-prompt` - 外部LLM开发原则和标准

| 路径 | 用途 | 读者 | 更新频率 |
|------|------|------|----------|
| `$PROJECT_ROOT/.claude/coding-prompt/Virtues.md` | 核心开发原则 | Claude AI、开发者 | 子模块更新时 |
| `$PROJECT_ROOT/.claude/coding-prompt/README.md` | 子模块说明 | 开发者 | 子模块更新时 |
| `$PROJECT_ROOT/.claude/coding-prompt/LICENSE` | 许可证 | 开发者 | 子模块更新时 |

**注意**: 此子模块通过Git管理，内容来自外部仓库。

### Category C: 文档模板 (doc-template/)

**模板根目录**:
| 路径 | 用途 |
|------|------|
| `$PROJECT_ROOT/.claude/doc-template/README.md` | 模板使用说明 |

**开发相关模板** (`development/`):
| 路径 | 用途 |
|------|------|
| `$PROJECT_ROOT/.claude/doc-template/development/code_review_template.md` | 代码评审模板 |
| `$PROJECT_ROOT/.claude/doc-template/development/phase_report_template.md` | 阶段报告模板 |
| `$PROJECT_ROOT/.claude/doc-template/development/test_report_template.md` | 测试报告模板 |

**通用文档模板** (`general/`):
| 路径 | 用途 |
|------|------|
| `$PROJECT_ROOT/.claude/doc-template/general/CHANGELOG_template.md` | 变更日志模板 |
| `$PROJECT_ROOT/.claude/doc-template/general/CONTRIBUTING_template.md` | 贡献指南模板 |
| `$PROJECT_ROOT/.claude/doc-template/general/README_template.md` | README模板 |

**项目文档模板** (`project/`):
| 路径 | 用途 |
|------|------|
| `$PROJECT_ROOT/.claude/doc-template/project/api_doc_template.md` | API文档模板 |
| `$PROJECT_ROOT/.claude/doc-template/project/design_spec_template.md` | 设计规范模板 |
| `$PROJECT_ROOT/.claude/doc-template/project/development_plan_template.md` | 开发计划模板 |
| `$PROJECT_ROOT/.claude/doc-template/project/project_state_template.md` | 项目状态模板 |
| `$PROJECT_ROOT/.claude/doc-template/project/requirements_template.md` | 需求文档模板 |
| `$PROJECT_ROOT/.claude/doc-template/project/todo_template.md` | TODO模板 |

### Category D: 项目规范 (project-guideline/)

| 路径 | 用途 | 读者 |
|------|------|------|
| `$PROJECT_ROOT/.claude/project-guideline/README.md` | 规范使用指南 | 开发者、Claude AI |
| `$PROJECT_ROOT/.claude/project-guideline/coding_standards.md` | 编码标准（基于Virtues） | 开发者、Claude AI |
| `$PROJECT_ROOT/.claude/project-guideline/workflow_guide.md` | 5阶段敏捷开发流程 | Claude AI、项目经理 |
| `$PROJECT_ROOT/.claude/project-guideline/ai_interaction_guide.md` | AI协作最佳实践 | 开发者、Claude AI |

### Category E: 专项文档 (docs/)

| 路径 | 用途 | 读者 |
|------|------|------|
| `$PROJECT_ROOT/.claude/docs/INTEGRATION_GUIDE.md` | 集成指南 | 开发者 |
| `$PROJECT_ROOT/.claude/docs/metadata_checker_demo.md` | 元数据检查器演示 | 开发者 |
| `$PROJECT_ROOT/.claude/docs/metadata_checker_guide.md` | 元数据检查器使用指南 | 开发者 |
| `$PROJECT_ROOT/.claude/docs/metadata_checker_README.md` | 元数据检查器说明 | 开发者 |

### Category F: 工具脚本 (scripts/)

**注意**: `setup_symlinks.py` 已被手动删除，此目录当前为空或包含其他工具。

### Category G: 配置文件

| 路径 | 用途 | 访问权限 |
|------|------|----------|
| `$PROJECT_ROOT/.claude/settings.local.json` | 本地配置 | 受限 |
| `$PROJECT_ROOT/.claude/.gitmodules` | Git子模块配置 | Git |

---

## Claude AI 工作流程

当Claude开始新的对话时，应按以下顺序阅读文档：

1. **首先**: 阅读 `$PROJECT_ROOT/.claude/claude_guide.md` - 了解如何使用项目文档
2. **然后**: 阅读 `$PROJECT_ROOT/.claude/project_state.md` - 了解当前状态
3. **根据任务**:
   - 实现新功能 → 阅读 `$PROJECT_ROOT/.claude/development_plan.md` + `$PROJECT_ROOT/.claude/design_spec.md`
   - 理解业务需求 → 阅读 `$PROJECT_ROOT/.claude/requirements.md`
   - 修复Bug → 阅读相关代码 + `$PROJECT_ROOT/.claude/project_state.md`
   - 遵循编码标准 → 阅读 `$PROJECT_ROOT/.claude/project-guideline/coding_standards.md`
   - 了解工作流程 → 阅读 `$PROJECT_ROOT/.claude/project-guideline/workflow_guide.md`

---

## 文档更新规则

| 文档 | 触发更新条件 | 更新人 |
|------|-------------|-------|
| `$PROJECT_ROOT/.claude/project_state.md` | 功能完成/状态变更 | Claude |
| `$PROJECT_ROOT/.claude/requirements.md` | 产品需求变更 | 产品经理 |
| `$PROJECT_ROOT/.claude/development_plan.md` | Phase完成/计划调整 | 项目经理 |
| `$PROJECT_ROOT/.claude/design_spec.md` | 架构变更/接口调整 | 架构师 |
| `$PROJECT_ROOT/.claude/claude_guide.md` | 文档结构调整 | Claude |
| `$PROJECT_ROOT/.claude/TODO.md` | 任务完成/需求新增 | Claude |

---

## 文件关系图

### 核心文档依赖关系

```
claude_guide.md (入口)
    ↓
project_state.md (当前状态)
    ↓
    ├─→ development_plan.md (开发计划)
    │       ↓
    │   design_spec.md (技术设计)
    │
    ├─→ requirements.md (业务需求)
    │
    └─→ project-guideline/
            ├─→ coding_standards.md (编码标准)
            ├─→ workflow_guide.md (工作流程)
            └─→ ai_interaction_guide.md (AI协作)
```

### 模板使用关系

```
doc-template/
├─→ development/
│   ├─→ code_review_template.md → 用于代码评审
│   ├─→ phase_report_template.md → 用于阶段报告
│   └─→ test_report_template.md → 用于测试报告
├─→ general/
│   ├─→ CHANGELOG_template.md → 用于变更日志
│   ├─→ CONTRIBUTING_template.md → 用于贡献指南
│   └─→ README_template.md → 用于README
└─→ project/
    ├─→ api_doc_template.md → 用于API文档
    ├─→ design_spec_template.md → 生成 design_spec.md
    ├─→ development_plan_template.md → 生成 development_plan.md
    ├─→ project_state_template.md → 生成 project_state.md
    ├─→ requirements_template.md → 生成 requirements.md
    └─→ todo_template.md → 生成 TODO.md
```

---

## 路径使用约定

### 逻辑路径表示

`$PROJECT_ROOT` 是项目根目录的逻辑表示，使用时需要根据实际环境替换：

```bash
# 示例环境
$PROJECT_ROOT = /path/to/your/project

# 引用文件
$PROJECT_ROOT/.claude/project_state.md
# 实际路径为: /path/to/your/project/.claude/project_state.md
```

### 路径引用示例

**推荐用法**（使用逻辑路径）:
```markdown
参见：$PROJECT_ROOT/.claude/project_state.md
```

**转换为实际路径**:
```bash
# 在文档或脚本中
PROJECT_ROOT="/path/to/your/project"
cat "$PROJECT_ROOT/.claude/project_state.md"
```

---

## 快速导航

### 按用途查找

**了解项目状态**:
- `$PROJECT_ROOT/.claude/project_state.md`
- `$PROJECT_ROOT/.claude/TODO.md`

**理解需求和设计**:
- `$PROJECT_ROOT/.claude/requirements.md`
- `$PROJECT_ROOT/.claude/design_spec.md`
- `$PROJECT_ROOT/.claude/development_plan.md`

**遵循开发规范**:
- `$PROJECT_ROOT/.claude/project-guideline/coding_standards.md`
- `$PROJECT_ROOT/.claude/project-guideline/workflow_guide.md`
- `$PROJECT_ROOT/.claude/coding-prompt/Virtues.md`

**创建新文档**:
- 模板位于: `$PROJECT_ROOT/.claude/doc-template/`

**配置和设置**:
- `$PROJECT_ROOT/.claude/settings.local.json`
- `$PROJECT_ROOT/.claude/.gitmodules`

### 按角色查找

**Claude AI必读**:
1. `$PROJECT_ROOT/.claude/claude_guide.md`
2. `$PROJECT_ROOT/.claude/project_state.md`
3. `$PROJECT_ROOT/.claude/project-guideline/coding_standards.md`

**开发者参考**:
1. `$PROJECT_ROOT/.claude/README.md`
2. `$PROJECT_ROOT/.claude/project-guideline/README.md`
3. `$PROJECT_ROOT/.claude/requirements.md`

**项目经理关注**:
1. `$PROJECT_ROOT/.claude/development_plan.md`
2. `$PROJECT_ROOT/.claude/TODO.md`
3. `$PROJECT_ROOT/.claude/project-guideline/workflow_guide.md`

---

## 文档迁移说明

本文档整合了原 `$PROJECT_ROOT/.claude/docs_structure.md` 的内容，并进行了以下改进：

1. **路径标准化**: 使用 `$PROJECT_ROOT` 逻辑路径表示
2. **结构优化**: 按类别组织，便于查找
3. **信息增强**: 添加了快速导航和使用约定
4. **完整覆盖**: 包含所有36个文件的路径

**原始文档**: `$PROJECT_ROOT/.claude/docs_structure.md` (已整合至本文档)

---

## 维护指南

### 更新本文档时

当以下情况发生时，应更新本文档：

1. **新增文件**: 添加到相应的分类中
2. **删除文件**: 从分类中移除
3. **移动文件**: 更新路径信息
4. **用途变更**: 更新文件描述

### 保持一致性

确保本文档与实际目录结构保持一致：

```bash
# 验证目录结构
tree $PROJECT_ROOT

# 检查文件数量
find $PROJECT_ROOT -type f | wc -l
```

---

## 附录: 完整文件列表

**所有文件路径（按字母序）**:

```
$PROJECT_ROOT/.claude/.gitmodules
$PROJECT_ROOT/.claude/MIGRATION_SUMMARY.md
$PROJECT_ROOT/.claude/PATH_REFERENCE.md (本文档)
$PROJECT_ROOT/.claude/README.md
$PROJECT_ROOT/.claude/TODO.md
$PROJECT_ROOT/.claude/claude_guide.md
$PROJECT_ROOT/.claude/coding-prompt/LICENSE
$PROJECT_ROOT/.claude/coding-prompt/README.md
$PROJECT_ROOT/.claude/coding-prompt/Virtues.md
$PROJECT_ROOT/.claude/design_spec.md
$PROJECT_ROOT/.claude/development_plan.md
$PROJECT_ROOT/.claude/doc-template/README.md
$PROJECT_ROOT/.claude/doc-template/development/code_review_template.md
$PROJECT_ROOT/.claude/doc-template/development/phase_report_template.md
$PROJECT_ROOT/.claude/doc-template/development/test_report_template.md
$PROJECT_ROOT/.claude/doc-template/general/CHANGELOG_template.md
$PROJECT_ROOT/.claude/doc-template/general/CONTRIBUTING_template.md
$PROJECT_ROOT/.claude/doc-template/general/README_template.md
$PROJECT_ROOT/.claude/doc-template/project/api_doc_template.md
$PROJECT_ROOT/.claude/doc-template/project/design_spec_template.md
$PROJECT_ROOT/.claude/doc-template/project/development_plan_template.md
$PROJECT_ROOT/.claude/doc-template/project/project_state_template.md
$PROJECT_ROOT/.claude/doc-template/project/requirements_template.md
$PROJECT_ROOT/.claude/doc-template/project/todo_template.md
$PROJECT_ROOT/.claude/docs/INTEGRATION_GUIDE.md
$PROJECT_ROOT/.claude/docs/metadata_checker_demo.md
$PROJECT_ROOT/.claude/docs/metadata_checker_guide.md
$PROJECT_ROOT/.claude/docs/metadata_checker_README.md
$PROJECT_ROOT/.claude/project-guideline/README.md
$PROJECT_ROOT/.claude/project-guideline/ai_interaction_guide.md
$PROJECT_ROOT/.claude/project-guideline/coding_standards.md
$PROJECT_ROOT/.claude/project-guideline/workflow_guide.md
$PROJECT_ROOT/.claude/project_state.md
$PROJECT_ROOT/.claude/requirements.md
$PROJECT_ROOT/.claude/settings.local.json
```

---

**文档版本**: 1.0
**最后更新**: 2025-12-26
**维护者**: 项目团队
