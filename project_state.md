# 项目状态

**更新时间**: {UPDATE_DATE}
**当前阶段**: {CURRENT_PHASE}
**状态**: {STATUS}

---

## 使用说明

本文档为项目状态模板，使用占位符标记需要替换的内容。

### 占位符说明

| 占位符 | 说明 | 示例 |
|--------|------|------|
| {PROJECT_NAME} | 项目名称 | 敏捷项目管理工具 |
| {UPDATE_DATE} | 更新日期 | 2024-12-25 |
| {CURRENT_PHASE} | 当前阶段 | Phase 5 - GUI开发 |
| {STATUS} | 项目状态 | 🟢 MVP完成/🟡 进行中/🔴 阻塞 |
| {TECH_STACK} | 技术栈描述 | Python 3.8+ |
| {INTERFACE_TYPE} | 界面类型 | CLI/GUI/Web |

### 填写示例

```markdown
# 敏捷项目管理工具 - 项目状态

**更新时间**: 2024-12-25
**当前阶段**: Phase 5 - GUI开发
**状态**: 🟢 MVP完成
```

---

## 快速概览

这是一个基于{TECH_STACK}的{PROJECT_TYPE}，提供{INTERFACE_TYPE}。

**核心功能**:
- {功能1}
- {功能2}
- {功能3}

**界面支持**:
- **{INTERFACE_1}**: {STATUS} ({说明})
- **{INTERFACE_2}**: {STATUS} ({说明})
- **{INTERFACE_3}**: {STATUS} ({说明})

---

## 当前状态

### 已完成 ✅

| Phase | 功能 | 完成日期 |
|-------|------|----------|
| {PHASE_NAME} | {功能描述} | {DATE} |
| {PHASE_NAME} | {功能描述} | {DATE} |
| {PHASE_NAME} | {功能描述} | {DATE} |

### 当前阶段 🔄

**{CURRENT_PHASE_NAME}**:

- [ ] {任务1}
- [ ] {任务2}
- [ ] {任务3}

详见: [{相关文档}]({LINK})

### 待开始 📋

1. **{PHASE_NAME}**: {任务描述}
2. **{PHASE_NAME}**: {任务描述}
3. **{PHASE_NAME}**: {任务描述}

详见: [{开发计划}]({LINK})

---

## 技术栈

| 类别 | 技术选择 | 版本 | 说明 |
|------|----------|------|------|
| {CATEGORY_1} | {TECH_1} | {VERSION} | {说明} |
| {CATEGORY_2} | {TECH_2} | {VERSION} | {说明} |
| {CATEGORY_3} | {TECH_3} | {VERSION} | {说明} |
| {CATEGORY_4} | {TECH_4} | {VERSION} | {说明} |

---

## 快速开始

### 安装

```bash
# 克隆仓库
git clone {REPO_URL}
cd {PROJECT_DIR}

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 安装依赖
pip install -r requirements.txt
```

### 配置

```bash
# 复制配置文件
cp config.example.yaml config.yaml

# 编辑配置
# 根据需要修改配置项
```

### 运行

```bash
# {模式1}模式
{COMMAND_1}

# {模式2}模式
{COMMAND_2}

# 查看帮助
{COMMAND_HELP}
```

---

## 文档结构

```
{PROJECT_NAME}/
├── .claude/                     # 核心项目文档
│   ├── claude_guide.md         # Claude使用指引
│   ├── project_state.md        # 本文件
│   ├── development_plan.md     # 开发计划
│   ├── design_spec.md          # 设计方案
│   └── docs_structure.md       # 文档结构
│
├── docs/                       # 产品文档
│   └── {PRODUCT_DOC}           # 产品需求文档
│
├── src/                        # 源代码
│   ├── module1/                # 模块1
│   │   ├── __init__.py
│   │   ├── main.py
│   │   └── ...
│   ├── module2/                # 模块2
│   └── module3/                # 模块3
│
├── tests/                      # 测试
│   ├── unit/                   # 单元测试
│   ├── integration/            # 集成测试
│   └── e2e/                    # 端到端测试
│
├── config/                     # 配置
│   ├── settings.yaml
│   └── settings.example.yaml
│
├── scripts/                    # 工具脚本
│   ├── setup.sh
│   └── deploy.sh
│
├── TODO.md                     # TODO跟踪
└── README.md                   # 项目说明
```

---

## 核心模块

| 模块 | 状态 | 说明 |
|------|------|------|
| {MODULE_1} | {STATUS} | {说明} |
| {MODULE_2} | {STATUS} | {说明} |
| {MODULE_3} | {STATUS} | {说明} |
| {MODULE_4} | {STATUS} | {说明} |

**状态说明**:
- ✅ 已完成
- 🔄 进行中
- 📋 计划中
- ⏸️ 暂停
- ❌ 已取消

---

## 代码统计

- **总代码行数**: {LINES}行
- **模块数**: {MODULE_COUNT}个
- **测试覆盖率**: {COVERAGE}%
- **文档完整度**: {DOCS}%

**代码分布**:
- {LANGUAGE_1}: {PERCENT}%
- {LANGUAGE_2}: {PERCENT}%
- 配置文件: {PERCENT}%

---

## 配置要求

### 环境要求

- **操作系统**: {OS_REQUIREMENTS}
- **运行时**: {RUNTIME_VERSION}
- **内存**: {MEMORY_REQUIREMENT}
- **磁盘空间**: {DISK_REQUIREMENT}

### 环境变量

```bash
{ENV_VAR_1}="{VALUE_1}"
{ENV_VAR_2}="{VALUE_2}"
{ENV_VAR_3}="{VALUE_3}"
```

**必填变量**:

| 变量名 | 说明 | 示例 |
|--------|------|------|
| {ENV_VAR_1} | {说明} | {示例值} |
| {ENV_VAR_2} | {说明} | {示例值} |

### 配置文件

**配置路径**: {CONFIG_PATH}

```yaml
{CATEGORY_1}:
  setting1: "value1"
  setting2: "value2"

{CATEGORY_2}:
  setting1: "value1"
```

**配置说明**:

| 配置项 | 说明 | 默认值 | 必填 |
|--------|------|--------|------|
| setting1 | 配置说明 | value1 | 是 |
| setting2 | 配置说明 | value2 | 否 |

---

## 外部依赖

### 依赖服务

| 服务 | 版本 | 用途 | 状态 |
|------|------|------|------|
| {SERVICE_1} | {VERSION} | {用途} | {STATUS} |
| {SERVICE_2} | {VERSION} | {用途} | {STATUS} |

### 第三方库

**主要依赖**:

```python
# requirements.txt
{LIBRARY_1}=={VERSION}
{LIBRARY_2}=={VERSION}
{LIBRARY_3}=={VERSION}
```

**开发依赖**:

```python
# requirements-dev.txt
{DEV_LIBRARY_1}=={VERSION}
{DEV_LIBRARY_2}=={VERSION}
```

---

## 已知问题

| 问题 | 严重程度 | 状态 | 计划修复 |
|------|----------|------|----------|
| {ISSUE_1} | 🔴高/🟡中/🟢低 | {STATUS} | {VERSION/DATE} |
| {ISSUE_2} | 🔴高/🟡中/🟢低 | {STATUS} | {VERSION/DATE} |

**严重程度说明**:
- 🔴 高：影响主要功能，需立即修复
- 🟡 中：影响部分功能，计划修复
- 🟢 低：不影响功能，低优先级

---

## 下一步行动

### 立即开始

1. **{TASK_1}**
   - 描述: {任务描述}
   - 优先级: 高/中/低
   - 预计时间: {TIME_ESTIMATE}

2. **{TASK_2}**
   - 描述: {任务描述}
   - 优先级: 高/中/低
   - 预计时间: {TIME_ESTIMATE}

### 后续计划

3. **{TASK_3}**
   - 描述: {任务描述}
   - 优先级: 高/中/低
   - 预计时间: {TIME_ESTIMATE}

4. **{TASK_4}**
   - 描述: {任务描述}
   - 优先级: 高/中/低
   - 预计时间: {TIME_ESTIMATE}

详见: [{开发计划}]({LINK})

---

## 性能指标

### 当前性能

| 指标 | 当前值 | 目标值 | 状态 |
|------|--------|--------|------|
| 响应时间 | {CURRENT} | {TARGET} | {STATUS} |
| 吞吐量 | {CURRENT} | {TARGET} | {STATUS} |
| 资源占用 | {CURRENT} | {TARGET} | {STATUS} |

### 性能优化记录

| 日期 | 优化项 | 优化前 | 优化后 | 提升 |
|------|--------|--------|--------|------|
| {DATE} | {ITEM} | {BEFORE} | {AFTER} | {IMPROVEMENT} |

---

## 质量指标

### 测试覆盖

| 类型 | 覆盖率 | 目标 | 状态 |
|------|--------|------|------|
| 单元测试 | {CURRENT}% | {TARGET}% | {STATUS} |
| 集成测试 | {CURRENT}% | {TARGET}% | {STATUS} |
| 端到端测试 | {CURRENT}% | {TARGET}% | {STATUS} |

### 代码质量

| 指标 | 当前值 | 目标值 | 状态 |
|------|--------|--------|------|
| 代码复杂度 | {CURRENT} | {TARGET} | {STATUS} |
| 代码重复率 | {CURRENT} | {TARGET} | {STATUS} |
| 技术债务 | {CURRENT} | {TARGET} | {STATUS} |

---

## 发布历史

| 版本 | 日期 | 主要变更 | 状态 |
|------|------|----------|------|
| {VERSION} | {DATE} | {CHANGES} | {STATUS} |
| {VERSION} | {DATE} | {CHANGES} | {STATUS} |
| {VERSION} | {DATE} | {CHANGES} | {STATUS} |

---

## 团队信息

### 核心团队

| 角色 | 姓名 | 联系方式 |
|------|------|----------|
| {ROLE_1} | {NAME} | {CONTACT} |
| {ROLE_2} | {NAME} | {CONTACT} |

### 贡献者

- {CONTRIBUTOR_1}
- {CONTRIBUTOR_2}
- {CONTRIBUTOR_3}

---

## 相关链接

- **项目主页**: {PROJECT_URL}
- **文档站点**: {DOCS_URL}
- **代码仓库**: {REPO_URL}
- **问题跟踪**: {ISSUES_URL}
- **CI/CD**: {CICD_URL}

---

## 更新历史

| 日期 | 变更 | 变更人 |
|------|------|--------|
| {UPDATE_DATE} | {变更描述} | {AUTHOR} |
| {UPDATE_DATE} | {变更描述} | {AUTHOR} |
| {UPDATE_DATE} | {变更描述} | {AUTHOR} |

---

**最后更新**: {UPDATE_DATE}
**更新人**: {AUTHOR}
**下次更新**: {NEXT_UPDATE_DATE}
