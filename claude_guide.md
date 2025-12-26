# Claude AI 使用指引

**最后更新**: 2025-12-24

本文档告诉Claude AI如何有效地使用本项目文档。

---

## 快速开始：Claude应该做什么

当用户开始新的对话时，Claude应该：

### 0. 首先读取开发规范

```bash
Read: $PROJECT_ROOT/.claude/coding-prompt/Virtues.md
Read: $PROJECT_ROOT/.claude/project-guideline/coding_standards.md
```

**重要**: 这些文件定义了项目的开发规范和质量标准，Claude必须首先遵守。

### 1. 读取本指引

```bash
Read: $PROJECT_ROOT/.claude/claude_guide.md
```

### 2. 读取TODO.md（用户需求和问题）

```bash
Read: $PROJECT_ROOT/.claude/TODO.md
```

**重要**: TODO.md是用户提报新需求和问题的主要入口，Claude必须检查是否有新的待处理项。

### 3. 读取项目状态

```bash
Read: $PROJECT_ROOT/.claude/project_state.md
```

### 4. 根据用户任务读取相关文档

| 用户任务类型 | Claude应该读取 |
|-------------|----------------|
| "实现新功能" | `$PROJECT_ROOT/.claude/development_plan.md` + `$PROJECT_ROOT/.claude/design_spec.md` |
| "理解需求" | `$PROJECT_ROOT/.claude/docs/需求文档_v6.md` |
| "修复Bug" | 相关代码文件 + `$PROJECT_ROOT/.claude/project_state.md` |
| "架构问题" | `$PROJECT_ROOT/.claude/design_spec.md` |
| "项目进度" | `$PROJECT_ROOT/.claude/development_plan.md` + `$PROJECT_ROOT/.claude/project_state.md` |
| "开始<模块>开发" | `$PROJECT_ROOT/.claude/design_spec.md` (模块对应部分) |

---

## 文档阅读顺序

### 场景1：用户要求实现新功能

```
1. $PROJECT_ROOT/.claude/claude_guide.md (本文件)
2. $PROJECT_ROOT/.claude/TODO.md (检查是否有相关需求)
3. $PROJECT_ROOT/.claude/project_state.md (当前状态)
4. $PROJECT_ROOT/.claude/development_plan.md (优先级和Phase)
5. $PROJECT_ROOT/.claude/design_spec.md (技术设计)
6. 相关代码文件 (已有实现)
```

### 场景2：用户询问项目需求

```
1. $PROJECT_ROOT/.claude/claude_guide.md
2. $PROJECT_ROOT/.claude/TODO.md (用户需求和问题列表)
3. $PROJECT_ROOT/.claude/docs/需求文档_v6.md
```

### 场景3：用户要求修复Bug

```
1. $PROJECT_ROOT/.claude/claude_guide.md
2. $PROJECT_ROOT/.claude/TODO.md (检查是否已有问题报告)
3. $PROJECT_ROOT/.claude/project_state.md
4. 报错的代码文件
5. $PROJECT_ROOT/.claude/design_spec.md (如果需要理解设计)
```

### 场景4：用户报告新问题

```
1. $PROJECT_ROOT/.claude/claude_guide.md
2. $PROJECT_ROOT/.claude/TODO.md (在末尾添加新问题)
3. 相关代码文件
4. 开始调查和修复
```

### 场景5：用户提出新需求

```
1. $PROJECT_ROOT/.claude/claude_guide.md
2. $PROJECT_ROOT/.claude/TODO.md (在末尾添加新需求)
3. $PROJECT_ROOT/.claude/project_state.md
4. $PROJECT_ROOT/.claude/development_plan.md (评估优先级)
5. 开始实现
```

### 场景6：用户要求添加功能

```
1. $PROJECT_ROOT/.claude/claude_guide.md
2. $PROJECT_ROOT/.claude/TODO.md (检查需求)
3. $PROJECT_ROOT/.claude/project_state.md
4. $PROJECT_ROOT/.claude/development_plan.md (Phase 5)
5. $PROJECT_ROOT/.claude/design_spec.md (UI抽象层设计)
6. 相关UI代码 (src/ui/)
```

---

## 核心文档说明

### $PROJECT_ROOT/.claude/TODO.md

**用途**: 用户提报新需求和报告问题的主要入口

**包含内容**:
- 新增需求和问题列表
- 已完成需求列表
- 已解决问题列表
- 需求状态统计

**何时更新**: 用户添加新需求/问题时，或Claude完成需求/修复问题后

**重要**: Claude必须在每次对话开始时读取此文件，检查是否有新的待处理项

### $PROJECT_ROOT/.claude/project_state.md

**用途**: 当前项目状态快照

**包含内容**:
- 已完成功能列表
- 当前阶段状态
- 待开始任务
- 技术栈
- 快速开始命令

**何时更新**: 每次功能完成或状态变更后

### $PROJECT_ROOT/.claude/development_plan.md

**用途**: 开发路线图和优先级

**包含内容**:
- Phase划分和状态
- 当前阶段详细任务
- 后续阶段规划
- 依赖关系

**何时更新**: 每个Phase完成时

### $PROJECT_ROOT/.claude/design_spec.md

**用途**: 技术架构和设计细节

**包含内容**:
- 系统架构图
- 模块设计
- 接口定义
- 数据模型
- 技术选型

**何时更新**: 架构变更时

### $PROJECT_ROOT/.claude/docs/需求文档_v6.md

**用途**: 完整的产品需求

**包含内容**:
- 业务背景
- 功能需求
- 数据模型
- 用户交互设计

**何时更新**: 需求变更时（版本号升级）

### $PROJECT_ROOT/.claude/TODO.md

**用途**: 原始需求和任务跟踪

**包含内容**:
- 原始需求列表
- Phase完成情况
- 待解决问题

**何时更新**: 任务完成时

---

## Claude工作流程

### 开始对话时

1. ✅ 读取 `$PROJECT_ROOT/.claude/claude_guide.md`
2. ✅ 读取 `$PROJECT_ROOT/.claude/project_state.md`
3. ✅ 确认用户的意图（开发/理解/修复）
4. ✅ 根据意图读取额外文档

### 实现功能时

1. ✅ 阅读相关设计 (`$PROJECT_ROOT/.claude/design_spec.md`)
2. ✅ 查看已有实现（相关代码文件）
3. ✅ 遵循架构设计（抽象层、模块分离）
4. ✅ 完成后更新 `$PROJECT_ROOT/.claude/project_state.md`

### 更新状态时

当Claude完成功能或状态变更时，应该：

```bash
# 编辑project_state.md
Edit: $PROJECT_ROOT/.claude/project_state.md
# 更新相应的状态信息
```

---

## 关键设计原则

基于 [LLM开发原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md) 和 [项目编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)。

### 1. 完整性与Definition of Done

**原则**: 只有完全集成、验证、清理完毕的代码才算"完成"。

**要求**:
- ✅ 核心功能按需求实现
- ✅ 所有占位符和Mock数据已替换
- ✅ 完整的测试通过（0失败，0意外跳过）
- ✅ 代码编译和运行成功
- ✅ 所有临时服务和进程已关闭

### 2. 整体上下文意识

**原则**: 在写代码前先理解其在系统架构中的位置和目的。

**要求**:
- ✅ 仔细审查现有代码库、工具库和架构文档
- ✅ 不确定时主动提问："是否有现有实现？"
- ✅ 优先使用现有、经过验证的模块和函数

### 3. 健壮性与谨慎

**原则**: 代码必须健壮、安全，优雅处理错误。

**要求**:
- ✅ 使用强类型（Python中使用类型注解）
- ✅ 严格验证所有外部输入
- ✅ 使用标准错误处理机制

### 4. 实用主义与简单性 (YAGNI)

**原则**: 严格遵守"你不会需要它"原则，避免过度工程化。

**要求**:
- ✅ 专注于当前明确定义的需求
- ✅ 选择最简单、最直接的解决方案

**注意**: YAGNI不能作为跳过测试、错误处理或创建不完整接口的借口。

### 5. 清晰与自文档化代码

**原则**: 好代码应该自解释，注释解释"为什么"而非"是什么"。

**要求**:
- ✅ 使用清晰无歧义的变量、函数、类名
- ✅ 只为复杂算法、业务逻辑上下文或技术决策添加注释
- ❌ 不使用元注释（如 `// 修复bug XX`），用Git追踪
- ❌ 不保留大块注释掉的旧代码

### 6. 测试驱动的勤勉

**原则**: 没有测试的代码默认是损坏的。

**要求**:
- ✅ 代码变更后执行**整个**测试套件
- ✅ 任何测试失败视为关键停止事件
- ✅ 修复**应用代码**使失败测试通过
- ✅ 永不修改测试文件来隐藏错误

### 7. 资源管理

**原则**: 做开发环境的负责任公民。

**要求**:
- ✅ 启动的临时服务任务完成后自动关闭
- ✅ 如需手动管理，提供清晰的启动/停止说明

### 8. 分层架构原则

**核心层与业务层分离**

- **核心层**：工作流、AI调用、文档管理、配置管理
- **业务层**：基于核心层构建的具体功能模块
- **表现层**：CLI、GUI等前端实现

### 9. 代码复用原则

**核心层代码在所有场景下共用**

不同表现层（CLI/GUI/Web）调用相同的核心层模块。

### 10. 配置管理原则

**统一配置入口**

使用配置模块统一管理所有配置项，避免分散和硬编码。

---

## 常见任务指南

### 任务1：实现功能

**步骤**:
1. 读取 `$PROJECT_ROOT/.claude/design_spec.md` - 模块对应部分
2. 读取 `$PROJECT_ROOT/.claude/development_plan.md` - 模块对应任务
3. 查看参考实现 (`src/xxx`) 作为参考
4. 实现功能，继承 `base/` 接口（对应接口）

### 任务2：添加新阶段

**步骤**:
1. 更新 `$PROJECT_ROOT/.claude/docs/需求文档_v6.md`
2. 在 `prompts/` 添加提示词
3. 更新 `src/workflow/stage.py` 阶段定义
4. 实现AI调用逻辑
5. 更新 `$PROJECT_ROOT/.claude/project_state.md`

### 任务3：修复Bug

**步骤**:
1. 定位Bug代码
2. 读取相关设计文档
3. 修复Bug
4. 添加测试（如需要）
5. 更新 `$PROJECT_ROOT/.claude/TODO.md` 标记完成

### 任务4：重构代码

**步骤**:
1. 读取 `$PROJECT_ROOT/.claude/design_spec.md` 确保符合架构
2. 进行重构
3. 确保所有UI实现仍然工作
4. 更新设计文档（如架构变更）

---

## 文件路径约定

### 相对路径规则

当Claude引用文件时，使用项目根目录作为基准：

```python
# ✅ 正确
src/ui/gui/main_window.py
$PROJECT_ROOT/.claude/project_state.md
$PROJECT_ROOT/.claude/docs/需求文档_v6.md

# ❌ 错误 - 使用绝对路径
/home/user/any/path/src/ui/gui/main_window.py
```

### 代码引用格式

在文档中引用代码位置时，使用：

```markdown
文件: src/ui/gui/main_window.py
行数: 第42-58行
```

---

## 更新文档的时机

### $PROJECT_ROOT/.claude/TODO.md

Claude应该在以下情况更新：
- ✅ 完成TODO中的需求
- ✅ 修复TODO中的问题
- ✅ 用户提供新需求时（添加到文档）

**如何添加新需求**:
```markdown
### [待实现] 需求标题

**类型**: 新功能 / 增强 / 优化
**优先级**: 高 / 中 / 低
**提出日期**: YYYY-MM-DD
**描述**: 详细描述需求
```

### $PROJECT_ROOT/.claude/project_state.md

Claude应该在以下情况更新：
- ✅ 完成一个Phase
- ✅ 实现重要功能
- ✅ 修复关键Bug
- ✅ 状态变更（进行中→完成）

### $PROJECT_ROOT/.claude/development_plan.md

Claude应该在以下情况更新：
- ✅ Phase完成
- ✅ 优先级调整
- ✅ 新增Phase

### $PROJECT_ROOT/.claude/design_spec.md

Claude应该在以下情况更新：
- ✅ 架构变更
- ✅ 新增模块
- ✅ 接口变更

---

## 示例对话流程

### 用户："我想要添加一个新功能：XXX"

**Claude的响应**:
```
1. 读取 $PROJECT_ROOT/.claude/claude_guide.md
2. 在 $PROJECT_ROOT/.claude/TODO.md 末尾添加新需求
3. 读取 $PROJECT_ROOT/.claude/project_state.md
4. 读取 $PROJECT_ROOT/.claude/development_plan.md (评估优先级)
5. 开始实现功能
```

### 用户："发现一个Bug：XXX"

**Claude的响应**:
```
1. 读取 $PROJECT_ROOT/.claude/claude_guide.md
2. 在 $PROJECT_ROOT/.claude/TODO.md 末尾添加问题报告
3. 读取相关代码文件
4. 开始调查和修复
```

### 用户："开始实现功能模块"

**Claude的响应**:
```
1. 读取 $PROJECT_ROOT/.claude/claude_guide.md
2. 读取 $PROJECT_ROOT/.claude/TODO.md (检查需求)
3. 读取 $PROJECT_ROOT/.claude/project_state.md
4. 读取 $PROJECT_ROOT/.claude/development_plan.md (Phase 5)
5. 读取 $PROJECT_ROOT/.claude/design_spec.md (UI抽象层)
6. 查看现有实现
7. 开始实现基础框架
```

### 用户："项目进度如何？"

**Claude的响应**:
```
1. 读取 $PROJECT_ROOT/.claude/claude_guide.md
2. 读取 $PROJECT_ROOT/.claude/TODO.md (需求和问题统计)
3. 读取 $PROJECT_ROOT/.claude/project_state.md
4. 读取 $PROJECT_ROOT/.claude/development_plan.md
5. 总结当前状态和下一步计划
```

---

## 提示词模板

当Claude不确定要做什么时，可以问用户：

```
我已阅读项目文档。当前项目处于 [状态]，
下一步计划是 [Phase X]。

您希望我：
1. 实现 [具体功能]
2. 修复 [问题]
3. 解释 [文档/代码]
4. 其他任务？

请告诉我具体需求。
```

---

## 常见问题

### Q: 我应该先读哪个文档？

A: 总是先读 `$PROJECT_ROOT/.claude/claude_guide.md` (本文件)，然后读 `$PROJECT_ROOT/.claude/project_state.md`。

### Q: 用户要求和设计冲突怎么办？

A: 优先遵循用户要求，但提醒用户设计变更的影响。

### Q: 我应该更新哪些文档？

A: 最低限度更新 `$PROJECT_ROOT/.claude/project_state.md`。如果架构变更，更新 `$PROJECT_ROOT/.claude/design_spec.md`。

### Q: 代码应该放在哪里？

A: 参考 `$PROJECT_ROOT/.claude/design_spec.md` 的目录结构部分。

### Q: 如何实现新的UI（如Web）？

A: 继承 `src/ui/base/` 的抽象接口，参考CLI实现。

---

## 总结

**Claude的黄金法则**:

1. 📖 先读文档，再写代码
2. 🏗️ 遵循架构设计
3. 🔄 复用已有代码
4. 📝 完成后更新状态
5. 🤔 不确定就问用户

**文档阅读优先级**:

```
0. $PROJECT_ROOT/.claude/coding-prompt/Virtues.md (通用开发原则)
   $PROJECT_ROOT/.claude/project-guideline/coding_standards.md (项目编码规范)
    ↓
1. $PROJECT_ROOT/.claude/claude_guide.md (本文件)
    ↓
2. $PROJECT_ROOT/.claude/project_state.md
    ↓
3. $PROJECT_ROOT/.claude/development_plan.md 或 $PROJECT_ROOT/.claude/design_spec.md
    ↓
4. 具体代码文件
```

---

## 相关文档索引

### 开发规范
- [LLM开发原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md) - 通用的AI开发规范（7大核心原则）
- [项目编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md) - 项目特定的编码标准
  - Python编码规范 (PEP 8)
  - 类型注解要求
  - 命名约定
  - 代码质量标准

### 工作流程
- [工作流指南]($PROJECT_ROOT/.claude/project-guideline/workflow_guide.md) - 详细的开发流程说明
  - 5阶段敏捷开发流程
  - 文档更新时机
  - 代码提交流程
  - 测试要求
- [AI交互规范]($PROJECT_ROOT/.claude/project-guideline/ai_interaction_guide.md) - 与Claude协作的最佳实践
  - 有效提问技巧
  - Prompt编写方法
  - 协作模式
  - 质量保证

### 文档模板
- [模板目录]($PROJECT_ROOT/.claude/doc-template/) - 所有文档模板
- [核心模板]($PROJECT_ROOT/.claude/doc-template/core/) - **设计方案、项目状态、开发计划**（从项目文档提取）
- [通用模板]($PROJECT_ROOT/.claude/doc-template/general/) - README、CHANGELOG、贡献指南
- [开发模板]($PROJECT_ROOT/.claude/doc-template/development/) - 阶段报告、代码审查、测试报告
- [项目模板]($PROJECT_ROOT/.claude/doc-template/project/) - 需求文档、设计文档、API文档

### 核心文档
- [$PROJECT_ROOT/.claude/TODO.md]($PROJECT_ROOT/.claude/TODO.md) - 需求和问题跟踪
- [$PROJECT_ROOT/.claude/project_state.md]($PROJECT_ROOT/.claude/project_state.md) - 项目状态
- [$PROJECT_ROOT/.claude/development_plan.md]($PROJECT_ROOT/.claude/development_plan.md) - 开发计划
- [$PROJECT_ROOT/.claude/design_spec.md]($PROJECT_ROOT/.claude/design_spec.md) - 技术设计
- [$PROJECT_ROOT/.claude/PATH_REFERENCE.md]($PROJECT_ROOT/.claude/PATH_REFERENCE.md) - 路径参考文档
