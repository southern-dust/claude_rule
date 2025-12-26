# 项目指南目录

本目录包含项目的开发规范和工作流程指南，供开发团队和AI助手参考。

## 目录内容

```
project-guideline/
├── README.md                    # 本文件
├── coding_standards.md          # 编码规范
├── workflow_guide.md            # 工作流指南
└── ai_interaction_guide.md      # AI交互规范
```

## 使用指南

### 对于开发人员

1. **首先阅读**: [coding_standards.md]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md) - 了解编码规范
2. **然后阅读**: [workflow_guide.md]($PROJECT_ROOT/.claude/project-guideline/workflow_guide.md) - 了解开发流程
3. **参考**: [ai_interaction_guide.md]($PROJECT_ROOT/.claude/project-guideline/ai_interaction_guide.md) - 如何与AI协作

### 对于Claude AI

Claude应在开始新对话时按以下顺序阅读：

1. [coding-prompt/Virtues.md]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md) - 通用AI开发原则
2. [coding_standards.md]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md) - 项目编码规范
3. [workflow_guide.md]($PROJECT_ROOT/.claude/project-guideline/workflow_guide.md) - 工作流程
4. [.claude/claude_guide.md]($PROJECT_ROOT/.claude/claude_guide.md) - 项目使用指引

## 文档说明

### coding_standards.md

基于 [LLM开发原则]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md)，定义项目特定的编码标准：

- 7大核心原则
- Python编码规范 (PEP 8)
- 类型注解要求
- 命名约定
- 项目目录结构
- 代码审查标准

### workflow_guide.md

详细的开发流程说明：

- 5阶段敏捷开发流程
- 文档更新规则
- 代码提交流程
- 测试要求
- 发布流程

### ai_interaction_guide.md

AI辅助开发最佳实践：

- 如何有效向Claude提问
- Prompt编写技巧
- 代码审查协作
- 文档生成规范

## 与其他文档的关系

```
项目文档体系
├── coding-prompt/              # 通用LLM开发规范
│   └── Virtues.md
├── project-guideline/          # 项目特定规范 (本目录)
│   ├── coding_standards.md    # 基于Virtues.md
│   ├── workflow_guide.md
│   └── ai_interaction_guide.md
├── .claude/                    # 项目核心文档
│   ├── claude_guide.md
│   ├── design_spec.md
│   └── development_plan.md
└── doc-template/       # 文档模板
    ├── general/
    ├── development/
    └── project/
```

## 更新规则

- **编码规范**: 当有新的编码标准或工具引入时更新
- **工作流指南**: 当开发流程变更时更新
- **AI交互规范**: 当发现更好的协作方式时更新

所有变更需要：
1. 更新版本号
2. 在变更历史中记录
3. 通知团队成员

## 贡献指南

如果你有改进建议：

1. Fork项目
2. 创建改进分支
3. 提交Pull Request
4. 说明改进理由和预期效果

## 相关链接

- [开发规范]($PROJECT_ROOT/.claude/coding-prompt/Virtues.md)
- [项目状态]($PROJECT_ROOT/.claude/project_state.md)
- [开发计划]($PROJECT_ROOT/.claude/development_plan.md)
- [文档模板]($PROJECT_ROOT/.claude/doc-template/)

---

**最后更新**: 2025-12-25
**维护者**: [项目团队]
