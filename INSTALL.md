# Cascade (级联战队) 安装指南

**版本**: cascade-hybrid v3.0
**框架**: super-team-builder v3.0
**平台**: Claude Code for Windows

---

## 📋 安装前准备

### 系统要求

- ✅ Claude Code 已安装
- ✅ Windows 11/10 操作系统
- ✅ 有管理员权限（复制文件需要）
- ✅ 目标目录可访问

### 安装位置

**本机安装路径**（根据用户要求）：
```
C:\Users\Mr.Chen\.claude\skills\        # 协调器Skill
C:\Users\Mr.Chen\.claude\agents\       # 专家Agent配置
```

**配置包位置**：
```
N:\编程备份\3.0团队\cascade-hybrid-team\
```

---

## 🚀 安装步骤

### Step 1️⃣：备份现有配置（可选）

> ⚠️ **注意**：用户要求**不要留老版本备份**，此步骤可跳过

如需备份，执行：
```bash
# 备份现有配置
mkdir -p "C:/Users/Mr.Chen/.claude/backup/$(date +%Y%m%d)"
cp -r "C:/Users/Mr.Chen/.claude/skills/cascade-coordinator" "C:/Users/Mr.Chen/.claude/backup/"
cp -r "C:/Users/Mr.Chen/.claude/agents/cascade-*.md" "C:/Users/Mr.Chen/.claude/backup/"
```
```

**预期输出**：
```
C:/Users/Mr.Chen/.claude/skills/cascade-coordinator/skill.md
```

### Step 3️⃣：安装专家Agent配置

```bash
# 创建目标目录（如果不存在）
mkdir -p "C:/Users/Mr.Chen/.claude/agents"

# 复制所有专家配置
cp "N:/编程备份/3.0团队/cascade-hybrid-team/agents/cascade-anchor.md" "C:/Users/Mr.Chen/.claude/agents/"
cp "N:/编程备份/3.0团队/cascade-hybrid-team/agents/cascade-atlas.md" "C:/Users/Mr.Chen/.claude/agents/"
cp "N:/编程备份/3.0团队/cascade-hybrid-team/agents/cascade-prism.md" "C:/Users/Mr.Chen/.claude/agents/"
cp "N:/编程备份/3.0团队/cascade-hybrid-team/agents/cascade-forge.md" "C:/Users/Mr.Chen/.claude/agents/"
cp "N:/编程备份/3.0团队/cascade-hybrid-team/agents/cascade-scale.md" "C:/Users/Mr.Chen/.claude/agents/"

# 验证安装
ls "C:/Users/Mr.Chen/.claude/agents/cascade-*.md"
```

**预期输出**：
```
C:/Users/Mr.Chen/.claude/agents/cascade-anchor.md
C:/Users/Mr.Chen/.claude/agents/cascade-atlas.md
C:/Users/Mr.Chen/.claude/agents/cascade-prism.md
C:/Users/Mr.Chen/.claude/agents/cascade-forge.md
C:/Users/Mr.Chen/.claude/agents/cascade-scale.md
```

### Step 4️⃣：验证安装

#### 方法1：通过文件系统验证

```bash
# 检查协调器
test -f "C:/Users/Mr.Chen/.claude/skills/cascade-coordinator/skill.md" && echo "✅ 协调器安装成功" || echo "❌ 协调器安装失败"

# 检查所有专家
test -f "C:/Users/Mr.Chen/.claude/agents/cascade-anchor.md" && echo "✅ Anchor安装成功" || echo "❌ Anchor安装失败"
test -f "C:/Users/Mr.Chen/.claude/agents/cascade-atlas.md" && echo "✅ Atlas安装成功" || echo "❌ Atlas安装失败"
test -f "C:/Users/Mr.Chen/.claude/agents/cascade-prism.md" && echo "✅ Prism安装成功" || echo "❌ Prism安装失败"
test -f "C:/Users/Mr.Chen/.claude/agents/cascade-forge.md" && echo "✅ Forge安装成功" || echo "❌ Forge安装失败"
test -f "C:/Users/Mr.Chen/.claude/agents/cascade-scale.md" && echo "✅ Scale安装成功" || echo "❌ Scale安装失败"
```

**预期输出**：
```
✅ 协调器安装成功
✅ Anchor安装成功
✅ Atlas安装成功
✅ Prism安装成功
✅ Forge安装成功
✅ Scale安装成功
```

#### 方法2：通过Claude Code验证

在Claude Code对话中输入：
```
/launch cascade-coordinator
```

**预期响应**：
协调器应该被识别并可以使用。

---

## ✅ 安装后验证

### 测试协调器

在Claude Code中执行以下测试：

#### 测试1：基本触发
```
使用级联战队帮我分析一个任务需求
```

**预期结果**：
- 协调器应该被触发
- 进入需求沟通阶段
- 使用 AskUserQuestion 确认任务细节

#### 测试2：完整流程
```
使用级联战队开发一个简单的计算器功能，需要支持加减乘除
```

**预期结果**：
- 协调器执行6A流程
- 依次触发 Anchor → Atlas → Prism → [审批] → Forge → Scale
- 每个阶段生成产出文档
- 最终交付完整报告

#### 测试3：并行模式
```
使用级联战队同时开发三个独立的API端点：用户列表、用户详情、用户创建
```

**预期结果**：
- 协调器识别为并行任务
- 同时触发3个Forge实例
- 汇总所有产出

---

## 🔧 配置文件说明

### 协调器配置

**位置**：`C:\Users\Mr.Chen\.claude\skills\cascade-coordinator\skill.md`

**核心配置**：
- name: `cascade-coordinator`
- description: 包含团队目标、协调职责、混合执行模式标识
- 支持3种执行模式：串行、并行、混合

### 专家Agent配置

**位置**：`C:\Users\Mr.Chen\.claude\agents\cascade-[expert].md`

**配置清单**：
| 文件 | Agent名称 | 角色 |
|------|----------|------|
| cascade-anchor.md | cascade-anchor | 需求对齐专家 |
| cascade-atlas.md | cascade-atlas | 架构设计专家 |
| cascade-prism.md | cascade-prism | 任务拆解专家 |
| cascade-forge.md | cascade-forge | 自动化执行专家 |
| cascade-scale.md | cascade-scale | 质量评估专家 |

---

## 📝 卸载指南

如需卸载级联战队：

```bash
# 删除协调器
rm -rf "C:/Users/Mr.Chen/.claude/skills/cascade-coordinator"

# 删除专家配置
rm "C:/Users/Mr.Chen/.claude/agents/cascade-anchor.md"
rm "C:/Users/Mr.Chen/.claude/agents/cascade-atlas.md"
rm "C:/Users/Mr.Chen/.claude/agents/cascade-prism.md"
rm "C:/Users/Mr.Chen/.claude/agents/cascade-forge.md"
rm "C:/Users/Mr.Chen/.claude/agents/cascade-scale.md"

# 验证卸载
ls "C:/Users/Mr.Chen/.claude/skills/" | grep cascade
ls "C:/Users/Mr.Chen/.claude/agents/" | grep cascade
```

**预期输出**：无结果（已完全卸载）

---

## 🐛 故障排查

### 问题1：协调器无法触发

**症状**：输入指令后协调器没有响应

**可能原因**：
- skill.md 文件路径不正确
- 文件格式错误
- YAML frontmatter 格式问题

**解决方案**：
```bash
# 检查文件是否存在
ls "C:/Users/Mr.Chen/.claude/skills/cascade-coordinator/skill.md"

# 检查文件格式
head -10 "C:/Users/Mr.Chen/.claude/skills/cascade-coordinator/skill.md"
```

### 问题2：专家Agent无法触发

**症状**：协调器报错找不到专家Agent

**可能原因**：
- Agent配置文件路径不正确
- 文件名不匹配
- YAML frontmatter 格式问题

**解决方案**：
```bash
# 检查所有专家文件
ls "C:/Users/Mr.Chen/.claude/agents/cascade-*.md"

# 检查文件格式
head -5 "C:/Users/Mr.Chen/.claude/agents/cascade-anchor.md"
```

### 问题3：MCP工具无法使用

**症状**：专家Agent报错MCP工具不可用

**可能原因**：
- MCP服务器未配置
- MCP工具未在tools字段中声明
- 协调器未授权

**解决方案**：
1. 检查MCP服务器配置
2. 检查Agent的tools字段
3. 确保协调器已明确授权

### 问题4：执行模式识别错误

**症状**：协调器选择了错误的执行模式

**可能原因**：
- 任务分析不准确
- 依赖关系理解错误

**解决方案**：
- 使用 AskUserQuestion 与用户确认
- 手动指定执行模式

---

## 📞 技术支持

如遇到安装问题：

1. **检查日志**：查看Claude Code的执行日志
2. **验证文件**：确保所有文件都已正确安装
3. **重启应用**：尝试重启Claude Code
4. **查阅文档**：阅读 README.md 了解团队使用方式

---

## 🔄 更新升级

当有新版本时：

```bash
# 1. 下载新配置包到 N:/编程备份/3.0团队/

# 2. 重新安装（覆盖旧版本）
cp -r "N:/编程备份/3.0团队/cascade-hybrid-team/skills/cascade-coordinator" "C:/Users/Mr.Chen/.claude/skills/"
cp "N:/编程备份/3.0团队/cascade-hybrid-team/agents/cascade-*.md" "C:/Users/Mr.Chen/.claude/agents/"

# 3. 验证更新
# 重复 "Step 4️⃣：验证安装"
```

---

## ✨ 安装完成

恭喜！级联战队已成功安装。

**下一步**：
1. 阅读 [README.md](README.md) 了解团队使用方式
2. 尝试使用协调器执行简单任务
3. 探索6A流程的各个阶段

**快速体验**：
```
使用级联战队帮我规划一个个人博客系统的开发任务
```

---

**安装版本**: cascade-hybrid v3.0
**安装日期**: 2026-03-01
**文档版本**: 1.0
