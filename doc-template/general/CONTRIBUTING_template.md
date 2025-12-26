# 贡献指南

感谢你有兴趣为本项目做出贡献！

我们欢迎各种形式的贡献，包括但不限于：

- 报告Bug
- 讨论代码状态
- 提交修复
- 提出新功能
- 成为维护者

## 开发环境设置

### 1. Fork并克隆仓库

```bash
# Fork本仓库到你的GitHub账号
# 然后克隆你的fork

git clone https://github.com/YOUR_USERNAME/PROJECT_NAME.git
cd PROJECT_NAME
```

### 2. 设置上游仓库

```bash
# 添加原始仓库作为upstream
git remote add upstream https://github.com/ORIGINAL_OWNER/PROJECT_NAME.git

# 验证远程仓库
git remote -v
```

### 3. 创建虚拟环境（Python项目）

```bash
# 使用venv
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 或使用conda
conda create -n project-name python=3.10
conda activate project-name
```

### 4. 安装依赖

```bash
# 安装项目依赖
pip install -r requirements.txt

# 安装开发依赖
pip install -r requirements-dev.txt
```

### 5. 安装pre-commit钩子（可选但推荐）

```bash
pip install pre-commit
pre-commit install
```

## 开发流程

### 1. 保持你的fork最新

```bash
# 获取上游变更
git fetch upstream

# 合并到你的本地主分支
git checkout master  # 或 main
git merge upstream/master
```

### 2. 创建特性分支

```bash
# 从master创建新分支
git checkout master
git checkout -b feature/your-feature-name

# 或修复bug
git checkout -b fix/bug-description
```

分支命名规范：

- `feature/` - 新功能
- `fix/` - Bug修复
- `docs/` - 文档更新
- `refactor/` - 代码重构
- `test/` - 测试相关
- `perf/` - 性能优化

### 3. 进行开发和测试

```bash
# 运行测试
pytest

# 运行代码检查
black .
flake8 .
mypy src/

# 或使用tox
tox
```

### 4. 提交变更

```bash
# 查看变更
git status
git diff

# 暂存文件
git add file1.py file2.py

# 提交变更
git commit -m "feat: add new feature description"
```

#### 提交信息规范

使用清晰的提交信息：

```bash
<类型>(<范围>): <简短描述>

<详细描述>

<关联问题>
```

类型（Type）：

- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档变更
- `style`: 代码格式（不影响功能）
- `refactor`: 重构
- `perf`: 性能优化
- `test`: 测试相关
- `chore`: 构建/工具相关

示例：

```bash
# 简单提交
git commit -m "fix: resolve memory leak in data processing"

# 详细提交
git commit -m "feat(auth): add OAuth2 authentication support

- Implement OAuth2 flow
- Add token refresh logic
- Update documentation

Closes #123"
```

### 5. 推送到你的fork

```bash
git push origin feature/your-feature-name
```

### 6. 创建Pull Request

1. 访问你fork的GitHub页面
2. 点击"Compare & pull request"
3. 填写PR模板
4. 等待代码审查

## Pull Request指南

### PR标题

使用清晰的标题：

```
[类型] 简短描述

示例：
[feat] Add user authentication
[fix] Resolve database connection timeout
```

### PR描述模板

创建PR时，请包含以下信息：

```markdown
## 变更类型
- [ ] Bug修复
- [ ] 新功能
- [ ] 代码重构
- [ ] 文档更新
- [ ] 性能优化

## 变更说明
描述你的变更是什么，为什么需要这个变更

## 相关问题
Closes #(issue number)

## 测试
描述你如何测试这些变更：
- [ ] 单元测试通过
- [ ] 手动测试步骤
- [ ] 添加了新的测试用例

## 截图（如适用）
添加截图或GIF展示变更效果

## 检查清单
- [ ] 代码符合项目编码规范
- [ ] 已添加必要的文档
- [ ] 所有测试通过
- [ ] 没有引入新的警告
```

## 代码规范

### 编码风格

请遵循项目的编码规范：

- Python项目遵循 [PEP 8](https://pep8.org/)
- JavaScript项目遵循 [Airbnb Style Guide](https://github.com/airbnb/javascript)
- 或参考项目特定的 `.editorconfig` 和 `.eslintrc` 配置

### 代码质量

- **命名**: 使用清晰、描述性的名称
- **注释**: 解释"为什么"而不是"是什么"
- **函数**: 保持函数简短，单一职责
- **测试**: 为新功能编写测试

详见 [项目编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)

### 代码格式化

```bash
# Python
black .
isort .

# JavaScript
npm run format

# 或使用pre-commit自动格式化
pre-commit run --all-files
```

## 测试要求

### 编写测试

- 为新功能添加单元测试
- 确保测试覆盖率不降低
- 使用有意义的测试名称

### 运行测试

```bash
# 运行所有测试
pytest

# 运行特定测试文件
pytest tests/test_specific.py

# 运行特定测试函数
pytest tests/test_specific.py::test_function

# 查看覆盖率
pytest --cov=src --cov-report=html
```

### 测试原则

- 遵循 AAA模式：Arrange, Act, Assert
- 测试应该快速且独立
- 使用mock隔离外部依赖

## 文档要求

- 更新相关的README文件
- 为公共API添加文档字符串
- 更新CHANGELOG.md
- 添加使用示例

## 报告Bug

### 报告前检查

- 搜索现有的Issue
- 确认不是重复问题
- 确认版本兼容性

### Bug报告模板

```markdown
**问题描述**
清晰简洁地描述问题

**复现步骤**
1. 步骤1
2. 步骤2
3. 步骤3

**期望行为**
描述你期望发生什么

**实际行为**
描述实际发生了什么

**环境信息**
- OS: [e.g. Ubuntu 20.04]
- Python版本: [e.g. 3.10]
- 项目版本: [e.g. v1.0.0]

**日志/截图**
粘贴相关日志或截图

**额外信息**
其他可能相关的信息
```

## 提出新功能

### 功能请求模板

```markdown
**功能描述**
清晰简洁地描述你想要的功能

**问题背景**
这个功能解决什么问题？为什么需要？

**建议的解决方案**
你希望如何实现这个功能

**替代方案**
你考虑过的其他解决方案

**附加信息**
示例、参考实现、相关Issue等
```

## 代码审查

### 作为贡献者

- 耐心等待审查反馈
- 及时回应评论
- 愿意根据反馈修改代码
- 保持开放和建设性的态度

### 作为审查者

- 保持友好和尊重
- 提供具体、可操作的建议
- 解释"为什么"而不仅仅是"怎么做"
- 认可好的代码

## 成为维护者

活跃的贡献者可能会被邀请成为维护者。维护者负责：

- 审查PR
- 合并代码
- 发布版本
- 管理Issue
- 引导新贡献者

## 行为准则

- 尊重所有贡献者
- 欢迎不同观点
- 建设性讨论
- 关注问题而不是人

如有违规行为，请联系项目维护者。

## 获取帮助

如果你有任何问题：

- 查看 [文档](README.md#文档)
- 搜索 [Issues](../../issues)
- 在Issue中提问
- 联系维护者

## 许可证

通过贡献代码，你同意你的贡献将根据项目的 [许可证](LICENSE) 进行许可。

---

再次感谢你的贡献！🎉

**最后更新**: YYYY-MM-DD
