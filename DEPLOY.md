# GitHub 部署指南

## 方式一：使用 GitHub MCP 自动部署（推荐）

### 1. 配置 GitHub 认证

在 Cursor 中配置 GitHub MCP 服务器，需要提供 GitHub Personal Access Token。

### 2. 执行部署命令

配置完成后，在 Cursor 中告诉 AI：
```
使用 GitHub MCP 将项目推送到 GitHub
```

AI 将自动：
- 创建 GitHub 仓库（如果不存在）
- 推送所有文件到仓库

---

## 方式二：手动部署

### 1. 初始化 Git 仓库（如果还没有）

```bash
git init
git add .
git commit -m "Initial commit: Multi-Agent Prompt Design"
```

### 2. 在 GitHub 上创建新仓库

1. 访问 https://github.com/new
2. 仓库名称：`Multi-Agent-Prompt-Design`
3. 描述：`多角色协作的数据库索引分析 Prompt 设计`
4. 选择 Public 或 Private
5. **不要**初始化 README、.gitignore 或 LICENSE（我们已经有了）
6. 点击 "Create repository"

### 3. 连接本地仓库到 GitHub

```bash
git remote add origin https://github.com/YOUR_USERNAME/Multi-Agent-Prompt-Design.git
git branch -M main
git push -u origin main
```

### 4. 验证部署

访问你的 GitHub 仓库，确认所有文件都已成功上传：
- ✅ README.md
- ✅ LICENSE
- ✅ Prompts/rule_db_index_analysis.md
- ✅ .gitignore

---

## 项目结构

部署后的项目结构：

```
Multi-Agent-Prompt-Design/
├── README.md                          # 项目主文档
├── LICENSE                            # MIT 许可证
├── .gitignore                        # Git 忽略文件
├── Prompts/
│   └── rule_db_index_analysis.md     # Prompt 规则文件
└── v1.md                             # 原始文档（可选保留）
```

---

## 后续更新

### 使用 Git 命令更新

```bash
git add .
git commit -m "更新描述"
git push
```

### 或使用 GitHub MCP

在 Cursor 中告诉 AI：
```
更新 GitHub 仓库：添加新的更改
```

