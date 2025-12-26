# Claude Rule - AI开发基础文档仓库

一个可复用的AI辅助开发文档库，专为集成到其他项目而设计。

**核心理念**：将本仓库 clone 到项目的 `.claude` 目录，通过符号链接将核心文档暴露在项目根目录，实现便捷访问和独立维护。

---

## 快速开始

### 在你的项目中集成此仓库

#### 方式一：直接 Clone（推荐用于快速开始）

```bash
# 在你的项目根目录
cd your-project

# 将本仓库 clone 为 .claude 目录
git clone https://github.com/your-username/claude_rule.git .claude
```

#### 方式二：Git 子模块（推荐用于正式项目）

```bash
# 在你的项目根目录
cd your-project

# 添加为 Git 子模块
git submodule add https://github.com/your-username/claude_rule.git .claude
git commit -m "Add claude_rule as git submodule"
```

#### 开始使用

现在你可以直接访问 `.claude/` 目录中的文档：

```bash
# 查看项目状态
cat .claude/project_state.md

# 添加新需求
vi .claude/TODO.md

# 查看 Claude 交互指南
cat .claude/claude_guide.md
```

---

## 集成效果

集成后的项目结构：

```
your-project/
├── .claude/                    # 📁 claude_rule 仓库（直接 clone 或子模块）
│   ├── README.md               # 使用指南
│   ├── claude_guide.md         # Claude AI 交互指南
│   ├── PATH_REFERENCE.md       # 项目路径参考
│   ├── project_state.md        # 项目状态
│   ├── design_spec.md          # 设计规格
│   ├── development_plan.md     # 开发计划
│   ├── requirements.md         # 需求文档
│   ├── TODO.md                 # 待办事项
│   ├── doc-template/           # 文档模板
│   ├── project-guideline/      # 项目规范
│   └── coding-prompt/          # 外部子模块（可选）
│
└── your-project-files/         # 你的项目文件
```

---

## 优势

- ✅ **简单集成**：一条命令即可完成集成（`git clone ... .claude`）
- ✅ **独立维护**：所有文档在 `.claude/` 目录中独立版本控制
- ✅ **清晰分离**：文档库与项目文件分离，结构清晰
- ✅ **统一更新**：通过 `git pull` 即可获取最新版本的文档模板
- ✅ **灵活使用**：既可以使用 clone 方式，也可以使用子模块方式

---

## 文档结构

本仓库包含以下内容：

### 核心文档

```
claude_rule/
├── README.md                   # 📚 本文件（Claude Rule 使用指南）
├── claude_guide.md             # 🤖 Claude AI 交互指南
├── PATH_REFERENCE.md           # 📁 项目路径参考
├── project_state.md            # 📊 项目状态模板
├── design_spec.md              # 🏗️ 设计规格模板
├── development_plan.md         # 📅 开发计划模板
├── requirements.md             # 📝 需求文档模板
└── TODO.md                     # ✅ 待办事项模板
```

### 支持文档和工具

```
claude_rule/
├── doc-template/              # 📋 文档模板库
│   ├── README.md
│   ├── general/               # 通用文档模板
│   ├── project/               # 项目文档模板
│   └── development/           # 开发文档模板
│
├── project-guideline/         # ⚙️ 项目规范
│   ├── README.md
│   ├── coding_standards.md    # 编码规范
│   ├── workflow_guide.md      # 工作流指南
│   └── ai_interaction_guide.md # AI 交互规范
│
├── coding-prompt/             # 🌐 外部子模块（可选）
│   └── Virtues.md             # 通用 LLM 原则
│
└── settings.local.json        # ⚙️ 本地配置
```

---

## 使用指南

### 对于项目开发者

#### 日常使用

1. **查看项目状态**
   ```bash
   cat .claude/project_state.md
   ```

2. **添加新需求**
   ```bash
   vi .claude/TODO.md
   ```

3. **查看设计文档**
   ```bash
   cat .claude/design_spec.md
   ```

4. **查看 Claude 交互指南**
   ```bash
   cat .claude/claude_guide.md
   ```

#### 更新文档库

**如果你使用的是直接 clone 方式：**
```bash
# 获取 claude_rule 的最新更新
cd .claude
git pull origin master
```

**如果你使用的是 Git 子模块方式：**
```bash
# 获取 claude_rule 的最新更新
git submodule update --remote .claude

# 或者进入子模块目录
cd .claude
git pull origin master
```

#### 编辑文档模板

直接在模板基础上编辑即可：

```bash
# 编辑项目状态
vi .claude/project_state.md

# 编辑 TODO
vi .claude/TODO.md
```

### 对于 Claude AI

每次对话开始时，Claude 应该按优先级阅读：

```
1. .claude/claude_guide.md                     # 核心 AI 交互指南
2. .claude/project-guideline/coding_standards.md # 编码规范
3. .claude/project_state.md                    # 当前项目状态
4. .claude/TODO.md                             # 待办事项
5. 其他相关文档（根据任务类型）
```

---

## 常见操作

### 更新本仓库（claude_rule 维护者）

```bash
# 在 claude_rule 仓库中
git add .
git commit -m "update core documentation"
git push origin master
```

### 在集成项目中同步更新

```bash
# 方式1：直接在 .claude 目录中更新
cd .claude
git pull origin master

# 方式2：如果使用子模块
git submodule update --remote .claude
```

### 移除集成

```bash
# 直接删除 .claude 目录
rm -rf .claude
```

### 无法推送更改到 .claude/

**问题**：直接 clone 的方式，更改需要推送到 claude_rule 仓库

**解决**：
```bash
# 方法1：在 .claude 目录中提交并推送到 claude_rule 仓库
cd .claude
git add .
git commit -m "update docs"
git push

# 方法2：如果只想在本项目中使用，不推送
# 直接修改 .claude/ 中的文件即可
# 但要注意下次 git pull 时可能会有冲突
```

---

## 相关资源

- [Git Submodule 文档](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
- [Claude Code 官方文档](https://github.com/anthropics/claude-code)
- [AI Prompt 最佳实践](https://github.com/Losses/coding-prompt)

---

## 贡献指南

欢迎贡献！请遵循：

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交变更 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

**贡献类型**：
- 新的模板
- 工作流改进
- 文档完善
- Bug 修复
- 示例项目

---

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

---

**维护者**: [southern-dust]
**最后更新**: 2025-12-26
**版本**: 0.0.1
