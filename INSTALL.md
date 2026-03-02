# Cascade (级联战队) 安装指南

## 安装步骤

### 1. 复制协调器 Skill

将协调器 Skill 复制到 Claude Code 的 skills 目录：

```bash
# Windows
cp -r "N:/编程备份/4.0团队/cascade-team/skills/cascade-coordinator" "$HOME/.claude/skills/"

# macOS/Linux
cp -r "/path/to/cascade-team/skills/cascade-coordinator" "$HOME/.claude/skills/"
```

### 2. 复制专家 Agents

将所有专家 Agent 复制到 Claude Code 的 agents 目录：

```bash
# Windows
cp "N:/编程备份/4.0团队/cascade-team/agents/"*.md "$HOME/.claude/agents/"

# macOS/Linux
cp "/path/to/cascade-team/agents/"*.md "$HOME/.claude/agents/"
```

### 3. 验证安装

确认以下文件已正确安装：

**Skills 目录**：
```
~/.claude/skills/cascade-coordinator/
└── skill.md
```

**Agents 目录**：
```
~/.claude/agents/
├── cascade-anchor.md
├── cascade-atlas.md
├── cascade-prism.md
├── cascade-forge.md
└── cascade-scale.md
```

### 4. 重启 Claude Code

重启 Claude Code 以加载新的配置。

## 一键安装命令（Windows）

```powershell
# 在 PowerShell 中执行
$skillsPath = "$env:USERPROFILE\.claude\skills\cascade-coordinator"
$agentsPath = "$env:USERPROFILE\.claude\agents"

# 创建目录（如果不存在）
New-Item -ItemType Directory -Force -Path $skillsPath
New-Item -ItemType Directory -Force -Path $agentsPath

# 复制文件
Copy-Item -Recurse -Force "N:\编程备份\4.0团队\cascade-team\skills\cascade-coordinator\*" $skillsPath
Copy-Item -Force "N:\编程备份\4.0团队\cascade-team\agents\*.md" $agentsPath

Write-Host "Cascade team installed successfully!"
```

## 一键安装命令（Git Bash / Linux / macOS）

```bash
#!/bin/bash

# 设置路径
SOURCE_DIR="N:/编程备份/4.0团队/cascade-team"
SKILLS_DIR="$HOME/.claude/skills/cascade-coordinator"
AGENTS_DIR="$HOME/.claude/agents"

# 创建目录
mkdir -p "$SKILLS_DIR"
mkdir -p "$AGENTS_DIR"

# 复制协调器 Skill
cp -r "$SOURCE_DIR/skills/cascade-coordinator/"* "$SKILLS_DIR/"

# 复制专家 Agents
cp "$SOURCE_DIR/agents/"*.md "$AGENTS_DIR/"

echo "Cascade team installed successfully!"
```

## 卸载

如需卸载，删除以下文件：

```bash
# 删除协调器 Skill
rm -rf "$HOME/.claude/skills/cascade-coordinator"

# 删除专家 Agents
rm -f "$HOME/.claude/agents/cascade-anchor.md"
rm -f "$HOME/.claude/agents/cascade-atlas.md"
rm -f "$HOME/.claude/agents/cascade-prism.md"
rm -f "$HOME/.claude/agents/cascade-forge.md"
rm -f "$HOME/.claude/agents/cascade-scale.md"
```

## 使用方法

安装完成后，可以通过以下方式触发团队：

### 方式1：使用协调器 Skill

```
/cascade-coordinator 我想开发一个用户认证系统
```

### 方式2：直接描述需求

```
请使用6A框架帮我开发一个博客系统
```

### 方式3：单阶段调用

```
帮我对齐这个项目的需求边界
帮我设计系统架构
帮我拆解任务
帮我实现这个功能
帮我评估代码质量
```

## 故障排查

### 问题1：协调器无法触发

**可能原因**：skill.md 未正确复制

**解决方案**：
```bash
# 检查文件是否存在
ls -la "$HOME/.claude/skills/cascade-coordinator/skill.md"
```

### 问题2：专家无法触发

**可能原因**：agent 文件未正确复制

**解决方案**：
```bash
# 检查文件是否存在
ls -la "$HOME/.claude/agents/cascade-"*.md
```

### 问题3：MCP 工具无法使用

**可能原因**：MCP 服务未配置

**解决方案**：检查 Claude Code 的 MCP 配置文件，确保以下服务可用：
- `mcp__sequential-thinking`
- `mcp__context7`
- `mcp__aurai-advisor`（可选）

## 版本信息

- **版本**：v4.0
- **更新日期**：2026-03-02
- **模板版本**：super-team-builder v3.0
