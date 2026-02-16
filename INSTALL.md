# Cascade 团队安装指南

## 前置条件

- Claude Code 已安装并正常运行
- 确认 `~/.claude/` 目录结构存在

## 安装步骤

### 步骤 1: 复制 Agent 配置

将 `agents/` 目录下的所有 `.md` 文件复制到 Claude Code 的 agents 目录：

```bash
# Windows (Git Bash)
cp -r cascade-team/agents/*.md ~/.claude/agents/

# macOS / Linux
cp -r cascade-team/agents/*.md ~/.claude/agents/
```

### 步骤 2: 复制 Skill 配置

将 `skills/cascade-coordinator/` 目录复制到 Claude Code 的 skills 目录：

```bash
# Windows (Git Bash)
cp -r cascade-team/skills/cascade-coordinator ~/.claude/skills/

# macOS / Linux
cp -r cascade-team/skills/cascade-coordinator ~/.claude/skills/
```

### 步骤 3: 验证安装

确认文件结构如下：

```
~/.claude/
├── agents/
│   ├── cascade-anchor.md
│   ├── cascade-atlas.md
│   ├── cascade-prism.md
│   ├── cascade-forge.md
│   └── cascade-scale.md
└── skills/
    └── cascade-coordinator/
        └── skill.md
```

### 步骤 4: 重启 Claude Code

重启 Claude Code 以加载新的团队配置。

### 步骤 5: 测试触发

在 Claude Code 中输入以下命令测试：

```
/cascade-coordinator

# 或者直接描述任务
帮我开发一个待办事项应用
```

## 触发关键词

### 协调器触发

| 关键词 | 说明 |
|--------|------|
| `/cascade-coordinator` | 显式调用协调器 |
| 项目开发 | 完整项目开发流程 |
| 全流程 | 启动6A全流程 |
| 级联战队 | 触发团队 |

### 各专家触发

| 专家 | 触发关键词 |
|------|------------|
| Anchor | 需求对齐、边界确认、需求分析、共识文档 |
| Atlas | 架构设计、系统设计、技术选型、接口定义 |
| Prism | 任务拆分、原子化、依赖分析、ToDoList |
| Forge | 代码实现、功能开发、测试编写 |
| Scale | 质量评估、验收测试、交付确认 |

## 使用示例

### 1. 启动完整项目

```
用户: 我想开发一个博客系统，请按照6A框架执行
协调器: 启动 Cascade 级联战队，开始6A全流程协作...
```

### 2. 单阶段调用

```
用户: 帮我设计这个系统的架构
协调器: 使用 cascade-atlas 专家进行架构设计...
```

### 3. 从中间阶段开始

```
用户: 我已经有需求文档了，帮我设计架构并拆解任务
协调器: 跳过 Align 阶段，从 Architect 阶段开始...
```

## 故障排除

### 问题: 专家没有被触发

**解决方案**:
1. 确认 `.md` 文件在正确目录
2. 确认文件格式正确（frontmatter + 内容）
3. 重启 Claude Code

### 问题: 协调器技能未出现

**解决方案**:
1. 确认 `skill.md` 在 `~/.claude/skills/cascade-coordinator/` 目录
2. 确认 skill.md 的 frontmatter 格式正确
3. 检查 Claude Code 的 skills 日志

### 问题: 工具权限错误

**解决方案**:
1. 检查各专家的 `tools` 配置
2. 确认 MCP 服务器已正确配置

## 卸载

如需卸载，删除以下文件：

```bash
# 删除 agents
rm ~/.claude/agents/cascade-*.md

# 删除 skill
rm -rf ~/.claude/skills/cascade-coordinator
```

## 更新

更新时，重新执行安装步骤即可覆盖旧文件。
