# OpenClaw-Android-Dev

OpenClaw Android 开发协作仓库 - 双端并行开发

## 项目概述

本项目是 OpenClaw-Android 的开发协作仓库，用于 WSL2 端和 Windows 端并行开发。

## 协作模式

| 端 | 职责 | 分支 |
|----|------|------|
| **WSL2** | 架构设计、验收测试 | `arch` |
| **Windows** | 代码实现、功能开发 | `impl` |

## 目录结构

```
/
├── specs/           # 架构规范（WSL2 维护）
│   ├── memory-system-spec.md
│   └── task-queue-spec.md
├── implementation/  # 代码实现（Windows 维护）
│   └── kotlin/
├── tests/           # 测试用例（WSL2 维护）
└── docs/            # 文档（共同维护）
```

## 当前进度

### ✅ 已完成
- [x] 记忆系统 Lite 架构设计
- [x] 任务队列 Lite 架构设计
- [x] 记忆系统代码实现
- [x] 任务队列代码实现
- [x] APK 编译验证

### 🔄 进行中
- [ ] BailianClient API 配置修复
- [ ] AgentSession 记忆注入集成

### 📋 待开发
- [ ] RAG 混合架构
- [ ] 语音交互
- [ ] 相机技能
- [ ] 离线推理

## 快速链接

- **APK 下载**: [腾讯云 COS](https://openclaw-1410633019.cos.ap-chengdu.myqcloud.com/OpenClaw-Android/latest/)
- **规范文件**: `/specs/`
- **Hub 协作**: `~/openclaw-hub/`

## 协作协议

1. **先回复确认，再执行**：收到消息后立即回复确认
2. **开发验证分离**：Windows 负责开发，WSL2 负责验证
3. **每小时同步**：定时任务检查进展并汇报

---

*创建时间: 2026-04-02*