# 编码规范

**项目名称**: claude_rule
**版本**: v1.0
**最后更新**: 2025-12-25

本文档定义项目的编码规范，基于 [LLM开发原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md)，结合项目特定需求制定。

---

## 核心原则

本项目遵循 [LLM Virtues]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md) 定义的7大核心原则：

### 1. 完整性与Definition of Done

**原则**: 只有完全集成、验证、清理完毕并准备交接的代码才算"完成"。

**具体要求**:
- ✅ 核心功能按需求实现
- ✅ 所有占位符和Mock数据已替换
- ✅ 完整的测试通过（0失败，0意外跳过）
- ✅ 代码编译和运行成功
- ✅ 所有临时服务和进程已关闭

**不接受的**:
- ❌ 声称任务完成但功能只部分实现
- ❌ 有任何测试失败就声称完成
- ❌ 用中间步骤或未完成提交来证明"重大里程碑"

### 2. 整体上下文意识

**原则**: 在写代码前先理解其在系统架构中的位置和目的。

**具体要求**:
- ✅ 仔细审查现有代码库、工具库和架构文档
- ✅ 不确定时主动提问："是否有现有实现？"
- ✅ 优先使用现有、经过验证的模块和函数

**不接受的**:
- ❌ 盲目重新实现已存在的功能
- ❌ 孤立地看待问题，忽略对其他模块的影响

### 3. 健壮性与谨慎

**原则**: 代码必须健壮、安全，优雅处理错误。

**具体要求**:
- ✅ 使用强类型（Python中使用类型注解）
- ✅ Rust中优先使用 `Result` 和 `Option`，避免 `.unwrap()`
- ✅ 其他语言使用标准错误处理机制
- ✅ 严格验证所有外部输入（API请求、用户输入）

**不接受的**:
- ❌ 为了"快速完成"牺牲类型安全或错误处理
- ❌ 提交可能导致panic或未处理异常的代码
- ❌ 过度简化导致处理边界情况时脆弱

### 4. 实用主义与简单性 (YAGNI)

**原则**: 严格遵守"你不会需要它"原则，避免过度工程化。

**具体要求**:
- ✅ 专注于当前明确定义的需求
- ✅ 选择最简单、最直接的解决方案

**不接受的**:
- ❌ 为"潜在未来需求"添加不必要的复杂性
- ❌ 需要简单方案时构建大型通用方案
- ❌ 用YAGNI作为跳过测试、错误处理或创建不完整接口的借口

### 5. 清晰与自文档化代码

**原则**: 好代码应该自解释，注释解释"为什么"而非"是什么"。

**具体要求**:
- ✅ 使用清晰无歧义的变量、函数、类名
- ✅ 只为复杂算法、业务逻辑上下文或技术决策添加注释

**不接受的**:
- ❌ 元注释如 `// 修复bug XX`（用Git）
- ❌ 重复代码的注释如 `i++; // i加1`
- ❌ 大块注释掉的旧代码
- ❌ 用前缀下划线或 `#[allow(dead_code)]` 来静默未使用代码警告

### 6. 测试驱动的勤勉

**原则**: 没有测试的代码默认是损坏的。

**具体要求**:
- ✅ 代码变更后执行**整个**测试套件（不用fail-fast）
- ✅ 任何测试失败视为关键停止事件
- ✅ 修复**应用代码**使失败测试通过
- ✅ 永不修改测试文件、注释掉断言或添加skip指令
- ✅ 迭代直到整个测试套件干净通过

**不接受的**:
- ❌ 提交没有对应测试的核心业务逻辑
- ❌ 把失败测试名解释为忽略、跳过或修改测试的理由
- ❌ 在第一次失败后停止测试执行
- ❌ 有任何测试失败时提交代码

### 7. 资源管理

**原则**: 做开发环境的负责任公民。

**具体要求**:
- ✅ 启动的临时服务（测试服务器、数据库连接）任务完成后自动关闭
- ✅ 如需手动管理，提供清晰的启动/停止说明

**不接受的**:
- ❌ 留下"僵尸进程"或后台服务运行

---

## Python编码规范

### PEP 8遵循

项目严格遵循 [PEP 8](https://pep8.org/) 风格指南。

**工具**: 使用 `black` 和 `flake8` 自动格式化和检查。

```bash
# 格式化代码
black .

# 检查代码
flake8 .
```

### 类型注解

**要求**: 所有公共函数必须有类型注解。

```python
# ✅ 正确
def calculate_discount(price: float, discount_rate: float) -> float:
    return price * (1 - discount_rate)

# ❌ 错误 - 缺少类型注解
def calculate_discount(price, discount_rate):
    return price * (1 - discount_rate)
```

**复杂类型使用 typing 模块**:

```python
from typing import List, Dict, Optional, Union

def process_items(
    items: List[Dict[str, Union[str, int]]],
    limit: Optional[int] = None
) -> List[str]:
    ...
```

### 命名约定

| 类型 | 约定 | 示例 |
|------|------|------|
| 模块 | 小写下划线 | `user_service.py` |
| 类 | 大驼峰 | `UserService` |
| 函数/方法 | 小写下划线 | `get_user()` |
| 常量 | 大写下划线 | `MAX_CONNECTIONS` |
| 私有成员 | 单下划线前缀 | `_internal_method()` |

### 文档字符串

使用 Google 风格的文档字符串：

```python
def create_user(username: str, email: str) -> User:
    """创建新用户。

    Args:
        username: 用户名，3-50个字符
        email: 邮箱地址

    Returns:
        创建的User对象

    Raises:
        ValueError: 如果用户名或邮箱格式不正确
        UserExistsError: 如果用户已存在
    """
    ...
```

### 错误处理

```python
# ✅ 正确 - 具体异常捕获
try:
    user = get_user(user_id)
except UserNotFoundError as e:
    logger.error(f"User not found: {user_id}")
    return None

# ❌ 错误 - 过于宽泛
try:
    user = get_user(user_id)
except Exception:
    pass

# ✅ 正确 - 明确错误信息
if not username:
    raise ValueError("Username cannot be empty")

# ❌ 错误 - 不明确的错误
if not username:
    raise Exception("Invalid input")
```

---

## 项目目录结构

```
claude_rule/
├── src/                    # 源代码
│   ├── ai/                # AI相关模块
│   ├── ui/                # UI层
│   │   ├── base/          # 抽象接口
│   │   ├── cli/           # CLI实现
│   │   └── gui/           # GUI实现
│   ├── workflow/          # 工作流引擎
│   ├── document/          # 文档管理
│   └── config/            # 配置管理
├── tests/                 # 测试代码
│   ├── unit/             # 单元测试
│   ├── integration/      # 集成测试
│   └── e2e/              # 端到端测试
├── docs/                  # 文档
├── scripts/               # 工具脚本
└── .claude/              # Claude AI相关文档
```

### 模块导入规范

```python
# 1. 标准库
import os
import sys
from pathlib import Path

# 2. 第三方库
import anthropic
from pydantic import BaseModel

# 3. 本地模块
from src.ai.client import AIClient
from src.workflow.engine import WorkflowEngine
```

---

## 代码质量标准

### 复杂度控制

- 函数长度: 不超过50行
- 函数参数: 不超过5个
- 嵌套层级: 不超过4层
- 圈复杂度: 不超过10

### DRY原则

```python
# ❌ 错误 - 重复代码
def process_user(user):
    email = user["email"]
    username = user["username"]
    ...

def process_admin(admin):
    email = admin["email"]
    username = admin["username"]
    ...

# ✅ 正确 - 提取公共逻辑
def process_person(person: dict) -> None:
    email = person["email"]
    username = person["username"]
    ...
```

### SOLID原则

- **S**ingle Responsibility: 每个类/函数只做一件事
- **O**pen/Closed: 对扩展开放，对修改关闭
- **L**iskov Substitution: 子类可替换父类
- **I**nterface Segregation: 接口小而专注
- **D**ependency Inversion: 依赖抽象而非具体实现

---

## 测试规范

### 测试命名

```python
def test_<function>_<scenario>_<expected_result>():
    """测试函数_场景_期望结果"""

# 示例
def test_create_user_with_valid_data_returns_user():
    ...

def test_create_user_with_duplicate_email_raises_error():
    ...

def test_create_user_with_empty_username_raises_validation_error():
    ...
```

### 测试结构

使用 AAA模式：Arrange, Act, Assert

```python
def test_calculate_discount_with_valid_rate():
    # Arrange - 准备测试数据
    price = 100.0
    discount_rate = 0.2

    # Act - 执行被测函数
    result = calculate_discount(price, discount_rate)

    # Assert - 验证结果
    assert result == 80.0
    assert result > 0
```

### 测试覆盖

目标覆盖率：
- 语句覆盖率: > 80%
- 分支覆盖率: > 75%
- 函数覆盖率: > 90%

```bash
# 生成覆盖率报告
pytest --cov=src --cov-report=html
```

---

## 代码审查检查清单

提交代码前确认：

### 功能性
- [ ] 实现了需求的所有功能
- [ ] 处理了边界情况
- [ ] 没有明显的逻辑错误

### 代码质量
- [ ] 遵循PEP 8规范
- [ ] 有适当的类型注解
- [ ] 命名清晰且一致
- [ ] 没有代码重复
- [ ] 函数职责单一

### 测试
- [ ] 有单元测试
- [ ] 测试覆盖正常和异常情况
- [ ] 所有测试通过

### 文档
- [ ] 公共API有文档字符串
- [ ] 复杂逻辑有注释
- [ ] README或相关文档已更新

### 安全
- [ ] 输入验证
- [ ] 没有硬编码的密钥/密码
- [ ] 错误处理恰当

---

## Git提交规范

### Commit Message格式

```
<类型>(<范围>): <简短描述>

<详细描述>

<关联问题>
```

### 类型（Type）

- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档变更
- `style`: 代码格式（不影响功能）
- `refactor`: 重构
- `perf`: 性能优化
- `test`: 测试相关
- `chore`: 构建/工具相关

### 示例

```bash
# 简单提交
git commit -m "fix: resolve memory leak in data processing"

# 详细提交
git commit -m "feat(ai): add streaming support for AI responses

- Implement SSE streaming for real-time output
- Add error handling for connection drops
- Update documentation

Closes #123"
```

---

## 工具配置

### Black (代码格式化)

`pyproject.toml`:
```toml
[tool.black]
line-length = 100
target-version = ['py310']
```

### isort (导入排序)

`pyproject.toml`:
```toml
[tool.isort]
profile = "black"
line_length = 100
```

### Flake8 (代码检查)

`.flake8`:
```ini
[flake8]
max-line-length = 100
extend-ignore = E203, W503
exclude = .git,__pycache__,build,dist
```

### mypy (类型检查)

`pyproject.toml`:
```toml
[tool.mypy]
python_version = "3.10"
warn_return_any = true
warn_unused_configs = true
disallow_untyped_defs = true
```

---

## 相关文档

- [LLM开发原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md)
- [工作流指南]($PROJECT_ROOT/.claude/project-guideline/workflow_guide.md)
- [AI交互规范]($PROJECT_ROOT/.claude/project-guideline/ai_interaction_guide.md)
- [项目设计文档]($PROJECT_ROOT/.claude/design_spec.md)

---

**维护者**: [项目团队]
**最后更新**: 2025-12-25
