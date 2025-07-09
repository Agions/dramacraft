# 🤝 贡献指南

感谢您对 DramaCraft 项目的关注！我们欢迎所有形式的贡献，包括但不限于代码、文档、测试、问题反馈和功能建议。

## 📋 目录

- [开发环境设置](#开发环境设置)
- [代码规范](#代码规范)
- [提交流程](#提交流程)
- [测试要求](#测试要求)
- [文档贡献](#文档贡献)
- [问题反馈](#问题反馈)
- [功能建议](#功能建议)

## 🛠️ 开发环境设置

### 系统要求

- **Python**: 3.9 或更高版本
- **操作系统**: macOS、Windows、Linux
- **内存**: 建议 8GB 或更多
- **存储**: 至少 2GB 可用空间

### 必需工具

```bash
# 1. 安装 uv (推荐的包管理器)
curl -LsSf https://astral.sh/uv/install.sh | sh

# 2. 安装 Git
# macOS: brew install git
# Ubuntu: sudo apt install git
# Windows: https://git-scm.com/download/win

# 3. 安装系统依赖
# macOS: brew install ffmpeg
# Ubuntu: sudo apt install ffmpeg libopencv-dev
# Windows: 下载 FFmpeg 并添加到 PATH
```

### 项目设置

```bash
# 1. Fork 并克隆项目
git clone https://github.com/YOUR_USERNAME/dramacraft.git
cd dramacraft

# 2. 设置上游仓库
git remote add upstream https://github.com/agions/dramacraft.git

# 3. 安装依赖
uv sync --all-extras

# 4. 安装开发工具
uv add --dev pre-commit
uv run pre-commit install

# 5. 验证安装
uv run dramacraft --version
uv run pytest --version
```

### 环境配置

```bash
# 1. 复制环境配置模板
cp .env.example .env

# 2. 编辑配置文件
# 填入您的 LLM API 密钥和其他配置
```

## 📝 代码规范

### Python 代码风格

我们使用以下工具确保代码质量：

- **Black**: 代码格式化
- **Ruff**: 代码检查和导入排序
- **mypy**: 类型检查
- **pytest**: 测试框架

### 代码规范要求

1. **类型注解**: 所有函数和方法必须有完整的类型注解
2. **文档字符串**: 使用中文编写详细的 docstring
3. **变量命名**: 使用英文命名，遵循 snake_case 风格
4. **注释**: 关键逻辑使用中文注释说明
5. **错误处理**: 适当的异常处理和日志记录

### 代码检查

```bash
# 运行所有代码检查
uv run pre-commit run --all-files

# 单独运行各项检查
uv run black --check src tests
uv run ruff check src tests
uv run mypy src
```

### 代码格式化

```bash
# 自动格式化代码
uv run black src tests
uv run ruff check --fix src tests
```

## 🔄 提交流程

### 分支策略

- **main**: 主分支，包含稳定的生产代码
- **develop**: 开发分支，包含最新的开发代码
- **feature/***: 功能分支，用于开发新功能
- **bugfix/***: 修复分支，用于修复问题
- **hotfix/***: 热修复分支，用于紧急修复

### 提交步骤

```bash
# 1. 创建功能分支
git checkout -b feature/your-feature-name

# 2. 进行开发
# ... 编写代码 ...

# 3. 运行测试
uv run pytest
uv run pre-commit run --all-files

# 4. 提交更改
git add .
git commit -m "feat: 添加新功能描述"

# 5. 推送分支
git push origin feature/your-feature-name

# 6. 创建 Pull Request
# 在 GitHub 上创建 PR，填写详细描述
```

### 提交信息规范

使用 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

```
<类型>[可选范围]: <描述>

[可选正文]

[可选脚注]
```

**类型说明：**
- `feat`: 新功能
- `fix`: 修复问题
- `docs`: 文档更新
- `style`: 代码格式调整
- `refactor`: 代码重构
- `test`: 测试相关
- `chore`: 构建或辅助工具更改

**示例：**
```
feat(llm): 添加腾讯混元大模型支持

- 实现腾讯混元 API 客户端
- 添加相应的配置选项
- 更新工厂方法以支持新提供商

Closes #123
```

## 🧪 测试要求

### 测试类型

1. **单元测试**: 测试单个函数或类的功能
2. **集成测试**: 测试模块间的交互
3. **端到端测试**: 测试完整的工作流程
4. **性能测试**: 测试系统性能和资源使用

### 测试覆盖率

- **最低要求**: 80% 代码覆盖率
- **目标**: 90% 代码覆盖率
- **关键模块**: 95% 代码覆盖率

### 运行测试

```bash
# 运行所有测试
uv run pytest

# 运行特定模块测试
uv run pytest tests/test_llm_integration.py

# 运行测试并生成覆盖率报告
uv run pytest --cov=dramacraft --cov-report=html

# 运行性能测试
uv run pytest tests/performance/ -v
```

### 编写测试

```python
import pytest
from dramacraft.llm.baidu import BaiduLLMClient

class TestBaiduLLMClient:
    """百度LLM客户端测试。"""
    
    @pytest.fixture
    def client(self):
        """创建测试客户端。"""
        config = {"api_key": "test", "secret_key": "test"}
        return BaiduLLMClient(config)
    
    @pytest.mark.asyncio
    async def test_generate_success(self, client):
        """测试成功生成。"""
        # 测试逻辑
        pass
```

## 📚 文档贡献

### 文档类型

1. **API 文档**: 模块和函数的详细说明
2. **使用教程**: 功能使用的步骤指南
3. **架构文档**: 系统设计和架构说明
4. **故障排除**: 常见问题和解决方案

### 文档规范

- **语言**: 使用专业的中文技术写作
- **格式**: Markdown 格式，遵循统一的样式
- **示例**: 提供完整可运行的代码示例
- **图片**: 使用高质量的图片和图表

### 文档构建

```bash
# 安装文档依赖
uv add --dev mkdocs mkdocs-material

# 本地预览文档
cd docs/website
mkdocs serve

# 构建文档
mkdocs build
```

## 🐛 问题反馈

### 报告问题

1. **搜索现有问题**: 确认问题未被报告
2. **使用问题模板**: 填写完整的问题信息
3. **提供详细信息**: 包含重现步骤、环境信息、错误日志
4. **添加标签**: 选择合适的问题类型标签

### 问题模板

```markdown
## 问题描述
简要描述遇到的问题

## 重现步骤
1. 执行命令 `...`
2. 配置参数 `...`
3. 观察到错误 `...`

## 预期行为
描述期望的正确行为

## 实际行为
描述实际发生的行为

## 环境信息
- 操作系统: 
- Python 版本: 
- DramaCraft 版本: 
- 相关依赖版本: 

## 错误日志
```
粘贴完整的错误日志
```

## 附加信息
其他可能有用的信息
```

## 💡 功能建议

### 提出建议

1. **描述需求**: 清楚说明功能需求和使用场景
2. **设计方案**: 提供初步的设计思路
3. **影响评估**: 分析对现有功能的影响
4. **实现难度**: 评估开发复杂度

### 建议模板

```markdown
## 功能描述
详细描述建议的新功能

## 使用场景
说明功能的具体使用场景和用户价值

## 设计方案
提供初步的技术设计方案

## API 设计
```python
# 示例 API 设计
def new_feature(param1: str, param2: int) -> Result:
    """新功能的 API 设计示例。"""
    pass
```

## 替代方案
是否有其他实现方式

## 影响评估
对现有功能和性能的影响
```

## 🎯 开发最佳实践

### 代码质量

1. **小步提交**: 每次提交包含单一逻辑变更
2. **测试驱动**: 先写测试，再写实现
3. **代码审查**: 认真对待代码审查反馈
4. **持续集成**: 确保 CI 检查通过

### 性能考虑

1. **异步优先**: 使用 async/await 处理 I/O 操作
2. **资源管理**: 及时释放资源，避免内存泄漏
3. **缓存策略**: 合理使用缓存提升性能
4. **监控指标**: 关注性能监控数据

### 安全要求

1. **输入验证**: 验证所有外部输入
2. **错误处理**: 避免泄露敏感信息
3. **依赖管理**: 及时更新安全补丁
4. **密钥管理**: 安全存储 API 密钥

## 📞 联系方式

- **GitHub Issues**: [问题反馈](https://github.com/agions/dramacraft/issues)
- **GitHub Discussions**: [讨论区](https://github.com/agions/dramacraft/discussions)
- **邮箱**: contact@dramacraft.com

感谢您的贡献！🎬✨
