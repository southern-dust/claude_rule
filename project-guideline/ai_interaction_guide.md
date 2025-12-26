# AI交互规范

**项目名称**: claude_rule
**版本**: v1.0
**最后更新**: 2025-12-25

本文档说明如何有效地与Claude AI协作开发。

---

## Claude工作流程

### 对话开始时

Claude应该按以下顺序阅读文档：

```
1. $PROJECT_ROOT/.claude/coding-prompt/Virtues.md           # 通用AI开发原则
2. $PROJECT_ROOT/.claude/project-guideline/coding_standards.md  # 项目编码规范
3. $PROJECT_ROOT/.claude/claude_guide.md            # 项目使用指引
4. $PROJECT_ROOT/.claude/project_state.md           # 当前项目状态
5. $PROJECT_ROOT/.claude/TODO.md                            # 用户需求和问题
```

### 根据任务类型读取额外文档

| 任务类型 | 额外读取 |
|---------|---------|
| 实现新功能 | $PROJECT_ROOT/.claude/development_plan.md + $PROJECT_ROOT/.claude/design_spec.md |
| 理解需求 | $PROJECT_ROOT/.claude/docs/需求文档_v6.md |
| 修复Bug | 相关代码文件 + $PROJECT_ROOT/.claude/project_state.md |
| 架构问题 | $PROJECT_ROOT/.claude/design_spec.md |
| 项目进度 | $PROJECT_ROOT/.claude/development_plan.md + $PROJECT_ROOT/.claude/project_state.md |

---

## 有效提问技巧

### 1. 提供上下文

**❌ 不好的提问**:
```
"我遇到了一个错误"
```

**✅ 好的提问**:
```
"在实现用户注册功能时，遇到了ValidationError。
我正在使用FastAPI，当POST /users时返回422错误。
相关代码在 src/api/users.py:45。
错误信息：..."
```

### 2. 明确目标

**❌ 不好的提问**:
```
"看看这个代码"
```

**✅ 好的提问**:
```
"请审查这段代码的性能问题。
这是一个订单处理函数，当前处理1000个订单需要5秒。
我希望优化到2秒以内。"
```

### 3. 分步骤提问

对于复杂任务，分解为小步骤：

```
# 第一步：理解
"请解释这段代码的工作原理"

# 第二步：改进
"基于你的理解，如何优化性能？"

# 第三步：实现
"请生成优化后的代码"
```

---

## Prompt编写最佳实践

### 功能实现Prompt模板

```
# 背景
[项目背景和相关文档链接]

# 任务
[具体任务描述]

# 要求
1. 遵循 [编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)
2. 包含完整的类型注解
3. 编写单元测试
4. 更新相关文档

# 约束
- 性能要求
- 兼容性要求
- 其他约束

# 输出格式
[期望的输出格式]
```

### 代码审查Prompt模板

```
请审查以下代码：
[代码或文件链接]

审查重点：
1. 是否符合 [编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)
2. 是否遵循 [Virtues原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md)
3. 性能、安全、可维护性

请使用 [代码审查模板]($PROJECT_ROOT/.claude/doc-template/development/code_review_template.md) 的格式输出。
```

### Bug修复Prompt模板

```
# Bug描述
[错误信息和现象]

# 复现步骤
1. 步骤1
2. 步骤2

# 期望行为
[期望结果]

# 相关代码
[代码链接或片段]

# 环境
- Python版本
- 依赖版本
- 操作系统
```

---

## 协作模式

### 模式1: Claude主导开发

适用场景：新功能实现、重构

```bash
# 用户指令
"实现用户认证功能，参考 design_spec.md 第3节"

# Claude流程
1. 读取相关文档
2. 询问不明确的地方
3. 设计实现方案
4. 编写代码和测试
5. 更新文档
6. 自我审查（对照 Virtues.md）
7. 报告完成情况
```

### 模式2: 辅助开发

适用场景：Bug修复、小改进

```bash
# 用户指令
"这个函数有内存泄漏，帮我修复"
[提供代码]

# Claude流程
1. 分析代码
2. 识别问题
3. 提供修复方案
4. 生成修复代码
5. 验证修复
```

### 模式3: 代码审查

适用场景：PR审查、代码质量检查

```bash
# 用户指令
"审查PR #123"
[提供PR链接或diff]

# Claude流程
1. 读取代码变更
2. 对照编码规范检查
3. 使用代码审查模板输出
4. 提供改进建议
```

---

## 文档生成规范

### API文档生成

```bash
# Prompt
"为以下函数生成API文档，
包含：参数说明、返回值、异常、示例"

# 输出格式（Google风格）
def function_name(param1: type, param2: type) -> return_type:
    """简短描述（一句话）。

    详细描述（可选）。

    Args:
        param1: 参数1说明
        param2: 参数2说明

    Returns:
        返回值说明

    Raises:
        ErrorType: 何时抛出

    Examples:
        >>> function_name(arg1, arg2)
        result
    """
```

### 测试用例生成

```bash
# Prompt
"为 [函数名] 生成完整的单元测试，
覆盖正常情况、边界情况、异常情况"

# 要求
- 使用pytest
- 遵循AAA模式（Arrange-Act-Assert）
- 测试命名：test_<function>_<scenario>_<expected>
```

### 文档更新提醒

Claude完成代码后应提醒用户更新：

```markdown
## 需要更新的文档

- [ ] [API文档]($PROJECT_ROOT/.claude/docs/api.md) - 新增端点
- [ ] [README.md]($PROJECT_ROOT/.claude/README.md) - 新功能说明
- [ ] [CHANGELOG.md]($PROJECT_ROOT/.claude/CHANGELOG.md) - 记录变更
```

---

## 质量保证

### 自我审查清单

Claude完成代码后应自查：

```markdown
## 自我审查

### Virtues原则检查
- [x] 完整性：所有功能实现，测试通过
- [x] 上下文：复用了现有代码
- [x] 健壮性：有错误处理
- [x] 简单性：没有过度工程化
- [x] 清晰性：命名清晰，注释适当
- [x] 测试：有完整的单元测试
- [x] 资源：没有遗留进程

### 编码规范检查
- [x] PEP 8格式
- [x] 类型注解完整
- [x] 文档字符串
- [x] 命名规范

### 测试检查
- [x] 所有测试通过
- [x] 覆盖率达标
- [x] 边界情况覆盖
```

### 测试执行

```bash
# Claude必须执行
pytest tests/ -v --cov=src

# 确认输出
✓ XX passed
✗ 0 failed
```

---

## 常见场景

### 场景1: 开始新功能

```bash
# 用户
"我想添加[功能]，从哪里开始？"

# Claude
1. 读取 TODO.md 确认是否有相关需求
2. 读取 development_plan.md 了解优先级
3. 读取 design_spec.md 了解架构
4. 引导用户走5阶段流程
```

### 场景2: 遇到错误

```bash
# 用户
"报错了：[错误信息]"

# Claude
1. 分析错误类型和原因
2. 提供可能的解决方案
3. 如果是代码问题，提供修复
4. 建议如何避免类似错误
```

### 场景3: 代码审查

```bash
# 用户
"请审查这段代码"
[代码]

# Claude
1. 检查编码规范
2. 检查Virtues原则
3. 提供具体改进建议
4. 使用模板输出报告
```

### 场景4: 重构建议

```bash
# 用户
"这段代码感觉有问题"
[代码]

# Claude
1. 识别问题（复杂度、重复、耦合）
2. 提出重构方案
3. 对比重构前后
4. 实施重构（如用户同意）
```

---

## 协作建议

### Do's（应该做的）

✅ **明确任务**: 清晰描述要做什么
✅ **提供上下文**: 提供相关文档和代码
✅ **分步进行**: 复杂任务分解为小步骤
✅ **反馈结果**: 告诉Claude结果如何
✅ **提问原因**: 不理解时问"为什么"

### Don'ts（不应该做的）

❌ **模糊指令**: "优化一下这个"（太模糊）
❌ **跳跃思维**: 一次提出多个不相关的任务
❌ **忽略规范**: 不让Claude遵循编码规范
❌ **跳过测试**: "不需要测试"（违背Virtues）
❌ **沉默对待**: Claude问问题时不回答

---

## 工具使用

### 文件操作

```bash
# 读取文件
Read: path/to/file.py

# 编辑文件
Edit: path/to/file.py
  old_string: "旧代码"
  new_string: "新代码"

# 写入文件
Write: path/to/file.py
  content: "完整内容"
```

### 代码执行

```bash
# 运行测试
Bash: pytest tests/unit/ -v

# 运行应用
Bash: python main.py

# 代码格式化
Bash: black .
```

### 搜索

```bash
# 搜索文件
Glob: **/*.py

# 搜索内容
Grep: pattern
```

---

## 相关文档

- [LLM开发原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md)
- [编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)
- [工作流指南]($PROJECT_ROOT/.claude/project-guideline/workflow_guide.md)
- [Claude使用指引]($PROJECT_ROOT/.claude/claude_guide.md)

---

## 示例对话

### 好的对话示例

```bash
# 用户
"我想实现用户注册功能，使用FastAPI。
需要邮箱验证，密码要加密。
参考 design_spec.md 第4节。"

# Claude
"我已经阅读了相关文档。
有几个问题需要确认：
1. 使用什么加密算法（bcrypt、argon2）？
2. 验证邮件有效期为多久？
3. 是否需要限制注册频率？"

# 用户
"1. bcrypt
2. 24小时
3. 是的，每IP每小时最多3次"

# Claude
"明白了。我将实现：
1. POST /users/register 端点
2. 邮箱验证服务
3. 限流中间件
4. 单元测试

开始实现..."
```

### 不好的对话示例

```bash
# 用户
"加个注册功能"

# Claude
"好的...（猜测实现）
[生成可能不符合需求的代码]"

# 用户
"不对，我要的是..."
```

---

**维护者**: [项目团队]
**最后更新**: 2025-12-25
