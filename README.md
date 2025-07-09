# 🎬 DramaCraft

**专业的短剧视频编辑 MCP 服务** - 集成剪映和国产中文大模型，实现智能视频编辑自动化

[![Python Version](https://img.shields.io/badge/python-3.9+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Documentation](https://img.shields.io/badge/docs-latest-brightgreen.svg)](https://dramacraft.readthedocs.io)
[![GitHub Stars](https://img.shields.io/github/stars/dramacraft/dramacraft.svg)](https://github.com/agions/dramacraft)

## ✨ 核心特性

### 🎯 智能视频编辑
- **🎤 智能解说生成** - 多种风格（搞笑、专业、情感）的解说文案自动生成
- **🎞️ 视频混剪制作** - 自动识别精彩片段，智能剪辑和拼接
- **📖 第一人称叙述** - 角色视角分析，生成沉浸式叙述内容
- **🎨 自动化特效** - 智能添加转场、滤镜和视觉效果

### 🔧 剪映深度集成
- **📁 标准格式支持** - 生成完全兼容的 `.draft` 文件
- **🚀 一键导入** - 自动导入剪映，无需手动操作
- **🎬 完整项目结构** - 支持剪映所有编辑功能
- **🔄 版本兼容** - 持续跟进剪映最新版本

### 🤖 国产大模型集成
- **🌟 百度千帆** - 完整的 API 集成和优化
- **⚡ 阿里通义** - 原生 SDK 支持
- **🚀 腾讯混元** - 专业级接口适配
- **🎯 智能切换** - 根据任务类型自动选择最优模型

### 🛠️ MCP 标准实现
- **📋 8个核心工具** - 涵盖视频编辑完整工作流
- **🔌 AI编辑器集成** - 支持 Cursor、Claude Desktop、VS Code 、trae
- **⚡ 异步处理** - 高性能并发架构
- **🔍 实时监控** - 完整的性能监控和错误恢复

## 🚀 快速开始

### 安装

```bash
# 使用 uv 安装（推荐）
uv add dramacraft

# 或使用 pip 安装
pip install dramacraft
```

### 配置

创建 `.env` 文件：

```env
# LLM 配置
LLM__PROVIDER=baidu
LLM__API_KEY=your_api_key_here
LLM__SECRET_KEY=your_secret_key_here

# 剪映配置
JIANYING__INSTALLATION_PATH=/Applications/JianyingPro.app

# 视频处理配置
VIDEO__TEMP_DIR=./temp
VIDEO__OUTPUT_DIR=./output
```

### 启动服务

```bash
# 启动 MCP 服务器
uv run dramacraft start

# 调试模式启动
uv run dramacraft start --debug

# 查看帮助
uv run dramacraft --help
```

## 🔌 AI 编辑器集成

### Cursor 配置

在 Cursor 设置中添加 MCP 服务器：

```json
{
  "mcpServers": {
    "DramaCraft": {
      "command": "uv",
      "args": ["run", "dramacraft", "start"],
      "env": {
        "LLM__PROVIDER": "baidu",
        "LLM__API_KEY": "your_api_key"
      }
    }
  }
}
```

### Claude Desktop 配置

在 `~/.config/claude-desktop/config.json` 中添加：

```json
{
  "mcpServers": {
    "DramaCraft": {
      "command": "uv",
      "args": ["run", "dramacraft", "start"],
      "env": {
        "LLM__PROVIDER": "baidu",
        "LLM__API_KEY": "your_api_key"
      }
    }
  }
}
```

### VS Code 配置

安装 MCP 扩展后，在设置中添加：

```json
{
  "mcp.servers": [
    {
      "name": "DramaCraft",
      "command": "uv",
      "args": ["run", "dramacraft", "start"]
    }
  ]
}
```

## 💡 使用示例

### 基础解说生成

```
用户: 帮我为这个短剧视频生成搞笑解说文案

AI: 我来为您生成搞笑解说文案。

[调用 generate_commentary 工具]
✅ 解说文案生成完成！

生成内容包括：
- 🎭 幽默开场白
- 🎯 关键情节解说
- 💬 互动元素设计
- 🎪 精彩结尾

文案已保存，可直接用于视频制作！
```

### 智能视频编辑

```
用户: 我有3个短剧片段，想制作一个2分钟的精彩合集

AI: 我来为您制作精彩合集！

[调用 smart_video_edit 工具]
🔍 正在分析视频内容...
✅ 识别出12个精彩片段
✅ 智能选择最佳8个片段
✅ 添加专业转场效果
✅ 生成配套解说文案
✅ 创建剪映项目文件
✅ 已自动导入剪映

您的精彩合集已准备就绪！可以在剪映中进一步编辑。
```

### 批量处理

```
用户: 我有一个短剧系列10集，想批量生成解说文案

AI: 我来批量处理您的短剧系列。

[调用 batch_process 工具]
📊 正在批量分析10个视频文件...
🎤 正在生成解说文案...
📁 正在创建剪映项目...

✅ 批量处理完成！
- 10个解说文案已生成
- 10个剪映项目已创建
- 1个系列预告片已制作

所有文件已保存到 output/ 目录。
```

## 🛠️ 核心工具

DramaCraft 提供 8 个专业的 MCP 工具：

| 工具 | 功能 | 描述 |
|------|------|------|
| `smart_video_edit` | 🎬 智能编辑 | 端到端自动化视频编辑流程 |
| `generate_commentary` | 🎤 解说生成 | 多风格智能解说文案生成 |
| `create_remix` | 🎞️ 混剪制作 | 自动识别精彩片段并制作合集 |
| `generate_narrative` | 📖 叙述生成 | 第一人称视角叙述内容生成 |
| `analyze_video` | 🔍 视频分析 | 深度视频内容分析和理解 |
| `create_jianying_draft` | 📁 草稿创建 | 创建标准剪映项目文件 |
| `control_jianying` | 🎮 剪映控制 | 自动化剪映软件操作 |
| `batch_process` | 📊 批量处理 | 高效批量处理多个视频 |

## 📊 性能特性

### ⚡ 高性能架构
- **异步处理** - 基于 asyncio 的高并发架构
- **智能缓存** - 自动缓存提升响应速度
- **资源管理** - 智能资源分配和清理
- **错误恢复** - 完善的错误处理和重试机制

### 📈 实时监控
- **性能指标** - CPU、内存、响应时间监控
- **任务跟踪** - 详细的任务执行统计
- **质量保证** - 多层次质量验证
- **日志记录** - 完整的操作日志

### 🔧 开发工具
```bash
# 系统诊断
uv run dramacraft doctor

# 配置验证
uv run dramacraft config --validate

# 工具测试
uv run dramacraft test --tool generate_commentary

# 性能监控
uv run dramacraft monitor --realtime
```

## 🏗️ 技术架构

### 模块化设计
```
dramacraft/
├── analysis/          # 视频内容深度分析
├── sync/             # 时间轴精确同步
├── audio/            # 智能音频增强
├── effects/          # 自动化特效系统
├── video/            # 剪映格式兼容
├── workflow/         # 端到端自动化
├── automation/       # 剪映自动化引擎
├── llm/              # 大模型集成
├── monitoring/       # 性能监控
└── utils/            # 工具库
```

### 核心技术
- **Python 3.9+** - 现代 Python 特性
- **AsyncIO** - 高性能异步处理
- **Pydantic** - 数据验证和序列化
- **OpenCV** - 视频处理和分析
- **FFmpeg** - 音视频编解码
- **MCP Protocol** - 标准化 AI 工具接口

## 📚 文档和资源

### 📖 完整文档
- [🚀 快速开始指南](docs/getting-started.md)
- [⚙️ 配置参考](docs/configuration.md)
- [🛠️ API 文档](docs/api/README.md)
- [💡 使用示例](docs/examples/README.md)
- [🔧 开发指南](docs/development.md)

### 🎯 实际应用
- [短剧系列制作](docs/examples/drama-series.md)
- [社交媒体内容](docs/examples/social-media.md)
- [教程视频制作](docs/examples/tutorial-videos.md)
- [精彩集锦制作](docs/examples/highlight-reels.md)

### 🔗 相关链接
- [GitHub 仓库](https://github.com/dramacraft/dramacraft)
- [在线文档](https://dramacraft.readthedocs.io)
- [问题反馈](https://github.com/dramacraft/dramacraft/issues)
- [更新日志](CHANGELOG.md)

## 🤝 贡献指南

我们欢迎所有形式的贡献！

### 🐛 报告问题
- 使用 [GitHub Issues](https://github.com/dramacraft/dramacraft/issues) 报告 bug
- 提供详细的重现步骤和环境信息
- 包含相关的日志和错误信息

### 💡 功能建议
- 在 Issues 中提出新功能建议
- 描述使用场景和预期效果
- 讨论实现方案和技术细节

### 🔧 代码贡献
```bash
# 1. Fork 项目
# 2. 创建功能分支
git checkout -b feature/amazing-feature

# 3. 提交更改
git commit -m 'Add amazing feature'

# 4. 推送到分支
git push origin feature/amazing-feature

# 5. 创建 Pull Request
```

### 📝 文档贡献
- 改进现有文档
- 添加使用示例
- 翻译文档到其他语言

## 📄 许可证

本项目采用 [MIT 许可证](LICENSE)。

## 🙏 致谢

感谢以下项目和社区的支持：

- [Model Context Protocol](https://modelcontextprotocol.io/) - 标准化 AI 工具接口
- [OpenCV](https://opencv.org/) - 计算机视觉库
- [FFmpeg](https://ffmpeg.org/) - 多媒体处理框架
- [Pydantic](https://pydantic.dev/) - 数据验证库
- [uv](https://github.com/astral-sh/uv) - 现代 Python 包管理器

## 📞 联系我们

- 📧 邮箱: contact@dramacraft.com
- 💬 GitHub Discussions: [讨论区](https://github.com/dramacraft/dramacraft/discussions)
- 🐛 问题反馈: [Issues](https://github.com/dramacraft/dramacraft/issues)

---

**DramaCraft** - 让 AI 助力您的视频创作！🎬✨

*Made with ❤️ by the Agions*
