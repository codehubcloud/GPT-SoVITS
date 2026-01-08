# 编码规范

本项目使用 [Ruff](https://docs.astral.sh/ruff/) 作为代码检查和格式化工具。

## 快速开始

### 安装 pre-commit hooks

```bash
pip install pre-commit
pre-commit install
```

### 手动运行检查

```bash
# 检查并自动修复所有文件
ruff check . --fix

# 格式化所有文件
ruff format .

# 或使用 pre-commit
pre-commit run --all-files
```

## 代码规范要点

### 1. 代码格式
- **行长度**: 最大 120 字符
- **缩进**: 4个空格
- **引号**: 优先使用双引号
- **Python版本**: Python 3.10+

### 2. Import 排序
Import 语句按以下顺序排列：
1. Future imports
2. 标准库
3. 第三方库
4. 本地项目导入

示例：
```python
from __future__ import annotations

import os
import sys

import torch
import numpy as np

from GPT_SoVITS.module import models
```

### 3. 命名规范
- **类名**: PascalCase (例如: `TextProcessor`)
- **函数/变量名**: snake_case (例如: `process_text`)
- **常量**: UPPER_SNAKE_CASE (例如: `MAX_LENGTH`)
- **私有成员**: 前缀下划线 (例如: `_internal_method`)

### 4. 类型注解
推荐使用类型注解提高代码可读性：

```python
def process_audio(file_path: str, sample_rate: int = 22050) -> np.ndarray:
    """处理音频文件"""
    pass
```

## 启用的规则

项目启用了以下 Ruff 规则集：
- **E/W**: pycodestyle (代码风格)
- **F**: Pyflakes (语法错误)
- **I**: isort (import排序)
- **N**: pep8-naming (命名规范)
- **UP**: pyupgrade (现代Python语法)
- **B**: flake8-bugbear (常见错误)
- **C4**: flake8-comprehensions (推导式优化)
- **SIM**: flake8-simplify (代码简化)
- **RUF**: Ruff特定规则

## 集成到编辑器

### VS Code
安装 Ruff 插件并在 `settings.json` 中添加：

```json
{
  "[python]": {
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll": true,
      "source.organizeImports": true
    },
    "editor.defaultFormatter": "charliermarsh.ruff"
  }
}
```

### PyCharm
1. 打开 Settings → Tools → External Tools
2. 添加 Ruff 作为外部工具
3. 配置快捷键

## 参考资料
- [Ruff 官方文档](https://docs.astral.sh/ruff/)
- [PEP 8 风格指南](https://pep8.org/)
