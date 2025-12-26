# 工作流指南

**项目名称**: claude_rule
**版本**: v1.0
**最后更新**: 2025-12-25

本文档详细说明项目的开发工作流程。

---

## 5阶段敏捷开发流程

项目采用AI辅助的5阶段敏捷开发方法：

### 阶段1: 需求分析 (Requirements)

**目标**: 理解并明确需求

**输入**:
- 用户需求描述
- 原始问题或想法

**输出**:
- 需求文档
- 用例列表

**活动**:
1. 收集和整理需求
2. 识别用户角色和使用场景
3. 定义验收标准
4. 更新 [TODO.md]($PROJECT_ROOT/.claude/TODO.md)

**负责人**: 产品经理 + AI助手

### 阶段2: 用户故事 (User Stories)

**目标**: 将需求转换为可执行的用户故事

**输入**:
- 需求文档

**输出**:
- 用户故事列表
- 验收标准

**用户故事模板**:
```
作为 [用户角色]
我想要 [执行某操作]
以便 [达成某目标]
```

**验收标准 (Given-When-Then)**:
```
Given [前置条件]
When [执行操作]
Then [期望结果]
```

**负责人**: 产品经理 + AI助手

### 阶段3: 概要设计 (High-Level Design)

**目标**: 设计系统架构和技术方案

**输入**:
- 用户故事列表
- 技术约束

**输出**:
- 架构图
- 模块划分
- 接口定义

**活动**:
1. 设计系统架构
2. 划分子系统和模块
3. 定义接口契约
4. 选择技术栈

**负责人**: 架构师 + AI助手

### 阶段4: 详细设计 (Detailed Design)

**目标**: 详细设计数据模型、API、算法

**输入**:
- 概要设计文档

**输出**:
- 数据模型设计
- API详细设计
- 关键算法设计

**活动**:
1. 设计数据模型和ER图
2. 定义REST API端点
3. 设计关键算法逻辑
4. 定义错误处理策略

**负责人**: 开发人员 + AI助手

### 阶段5: 设计实施 (Implementation)

**目标**: 生成代码实现

**输入**:
- 详细设计文档

**输出**:
- 可执行代码
- 单元测试
- 技术文档

**活动**:
1. 编写代码
2. 编写单元测试
3. 代码审查
4. 集成测试

**负责人**: 开发人员 + AI助手

---

## 文档更新规则

### 更新时机

| 文档 | 触发条件 | 更新人 |
|------|---------|--------|
| [TODO.md]($PROJECT_ROOT/.claude/TODO.md) | 任务完成/需求新增 | Claude |
| [project_state.md]($PROJECT_ROOT/.claude/project_state.md) | 功能完成/状态变更 | Claude |
| [development_plan.md]($PROJECT_ROOT/.claude/development_plan.md) | Phase完成/计划调整 | 项目经理 |
| [design_spec.md]($PROJECT_ROOT/.claude/design_spec.md) | 架构变更/接口调整 | 架构师 |
| [claude_guide.md]($PROJECT_ROOT/.claude/claude_guide.md) | 文档结构调整 | Claude |

### 更新流程

1. **完成任务后**:
   - 更新 project_state.md
   - 在 TODO.md 中标记完成
   - 如有架构变更，更新 design_spec.md

2. **Phase完成后**:
   - 更新 development_plan.md
   - 生成Phase报告（使用 [模板]($PROJECT_ROOT/.claude/doc-template/development/phase_report_template.md)）

3. **架构调整时**:
   - 更新 design_spec.md
   - 同步更新 docs_structure.md

---

## 代码提交流程

### 分支策略

```
master (main)
  ├── feature/xxx     # 新功能
  ├── fix/xxx         # Bug修复
  ├── refactor/xxx    # 重构
  └── docs/xxx        # 文档更新
```

### 提交流程

1. **创建分支**:
   ```bash
   git checkout master
   git pull origin master
   git checkout -b feature/your-feature
   ```

2. **开发和测试**:
   ```bash
   # 编写代码
   # 运行测试
   pytest

   # 代码格式化
   black .
   isort .

   # 类型检查
   mypy src/
   ```

3. **提交代码**:
   ```bash
   git add .
   git commit -m "feat: add new feature"
   ```

4. **推送并创建PR**:
   ```bash
   git push origin feature/your-feature
   # 在GitHub创建Pull Request
   ```

5. **代码审查**:
   - 使用 [代码审查模板]($PROJECT_ROOT/.claude/doc-template/development/code_review_template.md)
   - 至少1人审查通过

6. **合并代码**:
   - Squash merge to master
   - 删除feature分支

---

## 测试要求

### 测试金字塔

```
        /\
       /  \      E2E测试 (10%)
      /____\     - 关键用户流程
     /      \
    /        \   集成测试 (30%)
   /          \  - 模块间交互
  /____________\
                单元测试 (60%)
                - 函数/方法级别
```

### 测试执行顺序

1. **本地开发时**:
   ```bash
   # 快速反馈：只运行相关测试
   pytest tests/unit/test_specific.py -v
   ```

2. **提交前**:
   ```bash
   # 运行完整测试套件
   pytest
   ```

3. **CI/CD**:
   ```bash
   # 运行所有测试 + 覆盖率检查
   pytest --cov=src --cov-fail-under=80
   ```

---

## 发布流程

### 版本号规范

遵循语义化版本：`MAJOR.MINOR.PATCH`

- **MAJOR**: 不兼容的API变更
- **MINOR**: 向后兼容的新功能
- **PATCH**: 向后兼容的Bug修复

### 发布步骤

1. **准备发布**:
   ```bash
   # 确保在master分支
   git checkout master
   git pull origin master

   # 运行完整测试
   pytest
   ```

2. **更新版本号**:
   ```bash
   # 更新 __version__ 或 VERSION 文件
   # 更新 CHANGELOG.md
   ```

3. **创建发布标签**:
   ```bash
   git tag -a v1.0.0 -m "Release v1.0.0"
   git push origin v1.0.0
   ```

4. **GitHub Release**:
   - 创建GitHub Release
   - 附带CHANGELOG内容

5. **部署**:
   ```bash
   # 部署到生产环境
   ./scripts/deploy.sh production
   ```

---

## 故障排查流程

### Bug报告

1. **用户报告Bug**:
   - 在 TODO.md 中添加问题
   - 标记严重程度和优先级

2. **开发调查**:
   - 复现问题
   - 定位根本原因
   - 编写测试用例重现Bug

3. **修复Bug**:
   - 修复代码
   - 确保测试通过
   - 更新文档

4. **验证和关闭**:
   - 代码审查
   - 部署修复
   - 在 TODO.md 中标记已解决

---

## 性能优化流程

### 性能分析

1. **识别瓶颈**:
   ```bash
   # 使用cProfile分析
   python -m cProfile -o profile.stats your_script.py

   # 使用snakeviz可视化
   snakeviz profile.stats
   ```

2. **设定基准**:
   - 记录当前性能指标
   - 设定优化目标

3. **实施优化**:
   - 优化算法
   - 添加缓存
   - 数据库查询优化

4. **验证效果**:
   - 对比优化前后指标
   - 确保功能正常

---

## 相关文档

- [编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)
- [AI交互规范]($PROJECT_ROOT/.claude/project-guideline/ai_interaction_guide.md)
- [开发计划]($PROJECT_ROOT/.claude/development_plan.md)
- [项目状态]($PROJECT_ROOT/.claude/project_state.md)

---

**维护者**: [项目团队]
**最后更新**: 2025-12-25
