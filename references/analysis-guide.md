# 项目分析指南

## 首次分析步骤

重构启动时，按以下顺序分析项目：

### 1. 技术栈识别

```bash
# 查找配置文件识别框架
package.json / requirements.txt / Cargo.toml / go.mod / pom.xml / composer.json

# 查看框架配置
next.config.* / nuxt.config.* / vite.config.* / webpack.config.*
tsconfig.json / .babelrc / .eslintrc*
docker-compose.yml / Dockerfile
```

### 2. 项目结构扫描

```
# 关键目录
src/ | app/ | lib/ | pages/ | components/
api/ | routes/ | controllers/ | middleware/
models/ | schemas/ | migrations/
tests/ | __tests__ | spec/
config/ | env/
```

### 3. API路由发现

**Express/Koa/Hono:**
```bash
grep -r "router\.\(get\|post\|put\|delete\|patch\)" src/ --include="*.ts" --include="*.js"
grep -r "app\.\(get\|post\|put\|delete\|patch\)" src/ --include="*.ts" --include="*.js"
```

**Next.js:**
```bash
find src/app -name "route.ts" -o -name "route.js"
find pages/api -name "*.ts" -o -name "*.js"
```

**FastAPI/Django/Flask:**
```bash
grep -r "@app\.\(get\|post\|put\|delete\)" src/ --include="*.py"
grep -r "path\(" src/ --include="*.py"
```

### 4. 前端路由/页面发现

```bash
# React/Vue 路由
grep -r "Route\|router" src/ --include="*.tsx" --include="*.jsx" --include="*.vue"
grep -r "path:" src/ --include="*.tsx" --include="*.jsx" --include="*.vue"

# 页面组件
find src/pages src/app -name "*.tsx" -o -name "*.jsx" -o -name "*.vue"
```

### 5. 依赖分析

```bash
# 查看直接依赖
cat package.json | jq '.dependencies'
cat package.json | jq '.devDependencies'

# 查找废弃依赖
npx depcheck
```

### 6. 测试覆盖率

```bash
# 如有测试配置
npm test -- --coverage
pytest --cov
go test -cover
```

## 功能映射表

将分析结果填入以下结构：

```markdown
# {项目名} - 功能映射

## 后端模块

| 模块 | 路径 | 功能 | 关联前端 | 测试覆盖 |
|------|------|------|----------|----------|
| {name} | {path} | {func} | {frontend} | {coverage}% |

## API端点

| 端点 | 方法 | 认证 | 功能 | 前端调用 |
|------|------|------|------|----------|
| {path} | {method} | {auth} | {func} | {frontend_refs} |

## 前端页面

| 页面 | 路径 | 功能 | API依赖 |
|------|------|------|---------|
| {name} | {path} | {func} | {apis} |

## 数据流

{描述数据如何在前后端之间流动}

## 已知问题

1. {issue1}
2. {issue2}

## 优化建议

1. {suggestion1}
2. {suggestion2}
```
