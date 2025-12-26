# 文档模板目录

本目录包含项目常用的文档模板，用于规范文档格式和提高文档编写效率。

## 目录结构

```
doc-template/
├── general/           # 通用Markdown模板
│   ├── README_template.md
│   ├── CHANGELOG_template.md
│   └── CONTRIBUTING_template.md
├── development/       # 开发流程模板
│   ├── phase_report_template.md
│   ├── code_review_template.md
│   └── test_report_template.md
└── project/          # 项目文档模板
    ├── requirements_template.md
    ├── design_doc_template.md
    └── api_doc_template.md
```

## 使用方法

### 1. 选择合适的模板

根据你要编写的文档类型，从对应的子目录中选择模板：

- **通用文档** → `general/`
- **开发流程文档** → `development/`
- **项目设计文档** → `project/`

### 2. 复制模板并修改

```bash
# 示例：创建一个新的README
cp doc-template/general/README_template.md my-project/README.md

# 示例：创建一个阶段报告
cp doc-template/development/phase_report_template.md docs/phase1_report.md
```

### 3. 填充内容

按照模板中的提示，填充实际内容，删除不需要的部分。

### 4. 更新模板元数据

- 修改日期
- 更新版本号
- 填写作者信息
- 更新文档状态

## 模板说明

### general/ - 通用模板

适用于各种项目的通用文档：

- **README_template.md**: 项目主文档模板
- **CHANGELOG_template.md**: 版本更新记录模板
- **CONTRIBUTING_template.md**: 贡献指南模板

### development/ - 开发流程模板

适用于开发过程中的各类报告：

- **phase_report_template.md**: 开发阶段报告模板
- **code_review_template.md**: 代码审查报告模板
- **test_report_template.md**: 测试报告模板

### project/ - 项目文档模板

适用于项目特定的技术文档：

- **requirements_template.md**: 需求文档模板
- **design_doc_template.md**: 设计文档模板
- **api_doc_template.md**: API文档模板

## 更新规则

- 当发现模板需要改进时，可以直接修改
- 修改后更新本文档的版本号
- 重大变更需要在 `CHANGELOG_template.md` 中记录

## 模板设计原则

1. **简洁实用**: 只包含必要的章节，避免过度复杂
2. **易于定制**: 使用清晰的结构，便于根据项目需求调整
3. **中文友好**: 所有模板使用中文，符合项目文化
4. **示例完整**: 提供完整的示例内容，便于理解如何使用

## 相关文档

- [项目编码规范]($PROJECT_ROOT/.claude/project-guideline/coding_standards.md)
- [文档结构说明]($PROJECT_ROOT/.claude/PATH_REFERENCE.md)
- [开发流程指南]($PROJECT_ROOT/.claude/project-guideline/workflow_guide.md)

## 贡献指南

如果你有新的模板建议或改进意见：

1. Fork项目仓库
2. 创建新的模板或改进现有模板
3. 更新本README文件
4. 提交Pull Request

---

**最后更新**: 2025-12-25
