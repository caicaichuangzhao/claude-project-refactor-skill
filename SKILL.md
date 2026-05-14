---
name: project-refactor
description: |
  用于项目重构的全面跟踪与管理技能。
  当用户说 "重构项目"、"refactor"、"migrate"、"rewrite"、"upgrade project"、
  "项目升级"、"代码重构"、"重构进度"、"continue refactor"、"继续重构" 时自动激活。
  此技能跟踪重构状态、记录项目架构、API路由、前端接口和优化目标。
version: 1.0.0
---

# 项目重构技能 (Project Refactor Skill)

## 概述

此技能帮助系统性地进行项目重构，确保：
- 重构进度可追踪、可恢复
- 原有功能不被丢失
- 架构决策有记录
- API契约前后端一致
- 每次重构都让项目变得更好

## 激活条件

- 用户提及 "重构"、"refactor"、"migrate"、"rewrite"
- 需要查看重构进度或状态
- 继续之前的重构工作
- 分析项目架构或API

## 重构工作流

### 1. 初始化重构 (Start Refactor)

首次启动重构时执行：

```
/project-refactor init <项目名称>
```

自动分析：
1. 项目技术栈和架构
2. 主要功能模块
3. API路由列表
4. 前端页面/组件结构
5. 数据库/存储结构
6. 需要优化的点

生成文件：
- `.claude/refactor/<project>/REFACTOR.md` - 主跟踪文档
- `.claude/refactor/<project>/architecture.md` - 架构记录
- `.claude/refactor/<project>/api-routes.md` - API路由清单
- `.claude/refactor/<project>/frontend.md` - 前端结构
- `.claude/refactor/<project>/progress.md` - 进度跟踪

### 2. 查看重构状态 (Status)

```
/project-refactor status
```

显示：
- 当前重构阶段
- 已完成模块
- 正在进行中
- 待开始模块
- 阻塞问题

### 3. 继续重构 (Continue)

```
/project-refactor continue
```

自动读取进度文件，从上次中断处继续。

### 4. 记录模块完成 (Complete)

```
/project-refactor done <模块名>
```

更新进度，记录完成时间和变更摘要。

### 5. 添加优化目标 (Target)

```
/project-refactor target <优化描述>
```

记录需要优化的具体目标。

### 6. API对比检查 (API Check)

```
/project-refactor api-check
```

对比重构前后的API，确保兼容性。

## 重构数据结构

### REFACTOR.md 主文档结构

```markdown
# 项目重构：{项目名称}

- 开始时间：{date}
- 状态：{in-progress|paused|completed}
- 当前阶段：{phase}

## 重构目标

1. {目标1}
2. {目标2}

## 关键决策记录

| 日期 | 决策 | 原因 | 替代方案 |
|------|------|------|----------|
| {date} | {decision} | {reason} | {alternatives} |

## 风险与缓解

| 风险 | 影响 | 缓解措施 |
|------|------|----------|
| {risk} | {high/medium/low} | {mitigation} |

## 参考链接

- [架构文档](architecture.md)
- [API路由](api-routes.md)
- [前端结构](frontend.md)
- [进度跟踪](progress.md)
```

### progress.md 进度跟踪

```markdown
# 重构进度

## 总体进度: {completed}/{total} ({percentage}%)

## 模块清单

### {模块类别1}

- [x] {模块1} - {date} - {brief_summary}
- [ ] {模块2} - IN PROGRESS - {current_task}
- [ ] {模块3} - PENDING

### {模块类别2}

...

## 变更日志

### {date}

- {change_description}
- 影响：{affected_files}
- 回滚方式：{rollback_steps}

## 待解决问题

1. {issue1} - {priority}
2. {issue2} - {priority}

## 下次工作重点

{next_tasks}
```

### api-routes.md API清单

```markdown
# API路由清单

## 后端API

| 路由 | 方法 | 功能 | 状态 | 前端调用点 |
|------|------|------|------|------------|
| {path} | {GET/POST/...} | {function} | {original/refactored} | {frontend_refs} |

## 前端接口

| 页面/组件 | API依赖 | 重构状态 |
|-----------|---------|----------|
| {component} | {api_list} | {status} |

## API变更记录

| 日期 | API | 变更类型 | 前后对比 | 兼容性 |
|------|-----|----------|----------|--------|
| {date} | {api} | {add/modify/remove} | {before} → {after} | {breaking/non-breaking} |
```

### architecture.md 架构文档

```markdown
# 项目架构

## 技术栈

- 前端：{frontend_stack}
- 后端：{backend_stack}
- 数据库：{database}
- 其他：{others}

## 目录结构

```
{project_tree}
```

## 核心模块

### {模块1}

- 职责：{responsibility}
- 关键文件：{key_files}
- 依赖：{dependencies}
- 重构计划：{plan}

## 数据流

{diagram_or_description}

## 外部依赖

| 依赖 | 用途 | 版本 | 替换考虑 |
|------|------|------|----------|
| {dep} | {usage} | {version} | {notes} |
```

## 智能行为

### 自动激活时

当检测到重构相关关键词时：

1. **检查现有重构项目**
   - 扫描 `.claude/refactor/` 目录
   - 如果有进行中项目，提示继续

2. **新项目检测**
   - 分析当前目录结构
   - 识别项目类型
   - 询问是否启动重构跟踪

3. **重构上下文注入**
   - 读取相关跟踪文件
   - 提供当前进度上下文

### 重构质量保证清单

每个模块重构后必须检查：

- [ ] 原有功能完整保留
- [ ] API契约一致（如适用）
- [ ] 新增功能有测试
- [ ] 代码质量提升（可读性、性能）
- [ ] 文档已更新
- [ ] 回滚方案明确

### 重构完成标准

项目重构完全结束的条件：

1. 所有模块标记完成
2. 关键功能有回归测试
3. API兼容性验证通过
4. 性能基准不低于原版本
5. 文档已更新
6. 团队评审通过

## 最佳实践

1. **小步快跑**：每次只重构一个模块
2. **频繁验证**：重构后立刻测试
3. **记录决策**：所有架构决策记录原因
4. **保持向后兼容**：API变更需渐进式迁移
5. **性能监控**：重构前后对比性能指标

## 命令速查

| 命令 | 用途 |
|------|------|
| `/project-refactor init <name>` | 启动新重构项目 |
| `/project-refactor status` | 查看当前状态 |
| `/project-refactor continue` | 继续重构 |
| `/project-refactor done <module>` | 标记模块完成 |
| `/project-refactor target <desc>` | 添加优化目标 |
| `/project-refactor api-check` | API一致性检查 |
| `/project-refactor checkpoint` | 创建检查点 |
| `/project-refactor rollback` | 回滚到检查点 |
