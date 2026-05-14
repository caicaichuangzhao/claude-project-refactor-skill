# 重构记录模板

## 模块重构记录

```markdown
### 模块: {模块名称}

- 开始日期: {YYYY-MM-DD}
- 完成日期: {YYYY-MM-DD} (或 IN PROGRESS / BLOCKED)
- 负责人: {name} (可选)

#### 原始代码概要

- 位置: {file_path}
- 行数: {lines}
- 主要功能: {description}
- 关键问题: {issues_found}

#### 重构计划

1. {step1}
2. {step2}
3. {step3}

#### 重构后代码

- 位置: {new_file_path}
- 行数: {new_lines}
- 改进点: {improvements}

#### 变更文件

| 文件 | 变更类型 | 说明 |
|------|----------|------|
| {file} | {modified/new/deleted} | {description} |

#### 测试覆盖

- 重构前: {before_coverage}%
- 重构后: {after_coverage}%
- 新增测试: {test_files}

#### 性能对比

| 指标 | 重构前 | 重构后 | 变化 |
|------|--------|--------|------|
| {metric} | {before} | {after} | {change}% |

#### 备注

{any_notes}
```

---

## API变更记录模板

```markdown
### API: {METHOD} {endpoint}

- 日期: {YYYY-MM-DD}
- 变更类型: {added/modified/deprecated/removed}

#### 前 (Before)

```json
{request/response before}
```

#### 后 (After)

```json
{request/response after}
```

#### 迁移指南

{how_to_migrate}

#### 前端影响

| 前端文件 | 需要变更 | 说明 |
|----------|----------|------|
| {file} | {yes/no} | {details} |
```

---

## 问题记录模板

```markdown
### Issue: {title}

- 发现日期: {YYYY-MM-DD}
- 严重程度: {critical/high/medium/low}
- 状态: {open/in-progress/resolved/won't-fix}
- 涉及模块: {module}

#### 描述

{detailed_description}

#### 根因分析

{root_cause}

#### 解决方案

{solution}

#### 验证方式

{verification_steps}
```
