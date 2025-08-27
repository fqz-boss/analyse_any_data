# 📊 Analyse Any Data

> 智能数据分析工具 - 自动读取表格数据，生成多维度统计分析和切片报告

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-orange.svg)](https://github.com/fqz-boss/analyse_any_data)

## 🚀 项目简介

**Analyse Any Data** 是一个强大的数据分析工具，能够自动读取各种格式的表格数据，并生成全面的统计分析报告。无论是CSV、Excel还是其他格式的数据，都能轻松处理并提供深度洞察。

### ✨ 核心特性

- 📁 **多格式支持**: 支持 CSV、Excel (.xlsx, .xls)、TSV 等多种格式
- 🔍 **智能分析**: 自动识别数据类型，生成相应的统计指标
- 📈 **多维度切片**: 按不同维度对数据进行分组统计
- 📊 **可视化图表**: 生成直观的统计图表和报告
- 🎯 **异常检测**: 自动识别数据异常值和缺失值
- 📋 **详细报告**: 生成 HTML/PDF 格式的分析报告
- 💡 **智能建议**: 基于数据特征提供分析建议

## 🔧 功能模块

### 1. 数据读取模块
```python
from analyse_any_data import DataReader

# 支持多种格式
reader = DataReader()
data = reader.load_file("data.csv")  # CSV文件
data = reader.load_file("data.xlsx") # Excel文件
```

### 2. 基础统计分析
- **数值型数据**: 均值、中位数、众数、标准差、分位数
- **分类型数据**: 频次分布、唯一值统计、占比分析
- **时间序列数据**: 趋势分析、周期性检测

### 3. 多维度切片分析
```python
from analyse_any_data import Analyser

analyser = Analyser(data)
# 按单个维度切片
analyser.slice_by_dimension("category")
# 按多个维度交叉分析  
analyser.cross_analysis(["category", "region", "date"])
```

### 4. 数据质量检查
- 缺失值分析
- 重复数据检测
- 数据类型一致性检查
- 异常值识别

### 5. 可视化图表
- 柱状图、饼图、散点图
- 时间序列图
- 热力图、相关性矩阵
- 箱线图、小提琴图

## 📦 安装方式

### 环境要求
- Python 3.8+
- pandas >= 1.3.0
- numpy >= 1.20.0
- matplotlib >= 3.5.0
- seaborn >= 0.11.0
- plotly >= 5.0.0

### 快速安装
```bash
# 克隆项目
git clone https://github.com/fqz-boss/analyse_any_data.git
cd analyse_any_data

# 安装依赖
pip install -r requirements.txt

# 或者使用 conda
conda env create -f environment.yml
conda activate analyse_any_data
```

## 🎯 快速开始

### 基础用法

```python
from analyse_any_data import DataAnalyser

# 1. 加载数据
analyser = DataAnalyser("your_data.csv")

# 2. 生成基础统计报告
basic_stats = analyser.basic_statistics()
print(basic_stats)

# 3. 生成切片分析
slice_analysis = analyser.slice_analysis(
    dimensions=["category", "region"],
    metrics=["sales", "profit"]
)

# 4. 导出完整报告
analyser.generate_report(
    output_path="analysis_report.html",
    include_charts=True
)
```

### 高级用法

```python
# 自定义分析配置
config = {
    "chart_style": "seaborn",
    "color_palette": "husl",
    "figure_size": (12, 8),
    "export_format": ["html", "pdf"]
}

analyser = DataAnalyser("data.xlsx", config=config)

# 时间序列分析
if analyser.has_datetime_column():
    ts_analysis = analyser.time_series_analysis(
        date_column="date",
        value_column="sales",
        frequency="monthly"
    )

# 相关性分析
correlation_matrix = analyser.correlation_analysis()

# 异常检测
anomalies = analyser.detect_anomalies(method="isolation_forest")
```

## 📊 输出示例

### 基础统计信息
```
数据概览:
- 总行数: 10,000
- 总列数: 15
- 数值列: 8
- 分类列: 5  
- 日期列: 2

数据质量:
- 完整度: 95.2%
- 重复率: 0.8%
- 异常值: 123个
```

### 切片分析示例
```
按地区销售分析:
┌──────────┬──────────┬──────────┬──────────┐
│   地区   │   销量   │   占比   │   增长率 │
├──────────┼──────────┼──────────┼──────────┤
│   华东   │  25,680  │  32.1%   │  +15.6%  │
│   华南   │  19,450  │  24.3%   │  +8.9%   │
│   华北   │  18,920  │  23.6%   │  -2.1%   │
│   其他   │  15,950  │  19.9%   │  +21.3%  │
└──────────┴──────────┴──────────┴──────────┘
```

## 🏗️ 项目结构

```
analyse_any_data/
├── README.md
├── requirements.txt
├── setup.py
├── src/
│   ├── __init__.py
│   ├── data_reader.py      # 数据读取模块
│   ├── analyser.py         # 核心分析引擎
│   ├── visualizer.py       # 可视化模块
│   ├── reporter.py         # 报告生成模块
│   └── utils.py           # 工具函数
├── examples/
│   ├── basic_example.py
│   ├── advanced_example.py
│   └── sample_data/
├── tests/
│   ├── test_reader.py
│   ├── test_analyser.py
│   └── test_visualizer.py
└── docs/
    ├── user_guide.md
    ├── api_reference.md
    └── examples.md
```

## 🎨 支持的图表类型

| 图表类型 | 适用数据 | 用途 |
|---------|---------|------|
| 柱状图 | 分类数据 | 比较不同类别的数值 |
| 饼图 | 分类占比 | 显示各部分占整体的比例 |
| 散点图 | 数值数据 | 显示变量间的相关关系 |
| 时间序列图 | 时间数据 | 显示数据随时间的变化 |
| 箱线图 | 数值分布 | 显示数据的分布和异常值 |
| 热力图 | 矩阵数据 | 显示相关性或密度 |

## 🔍 使用场景

### 商业分析
- 销售数据分析
- 客户行为分析  
- 市场趋势分析
- 财务数据分析

### 学术研究
- 实验数据分析
- 问卷调查分析
- 统计建模
- 研究报告生成

### 日常办公
- Excel数据快速分析
- 数据质量检查
- 自动化报告生成
- 数据可视化

## 🤝 贡献指南

我们欢迎任何形式的贡献！

### 如何贡献
1. Fork 这个项目
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

### 开发环境设置
```bash
# 克隆项目
git clone https://github.com/fqz-boss/analyse_any_data.git
cd analyse_any_data

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate    # Windows

# 安装开发依赖
pip install -r requirements-dev.txt

# 运行测试
pytest tests/
```

## 📝 更新日志

### v1.0.0 (2025-08-27)
- 🎉 项目初始版本
- ✅ 支持CSV、Excel文件读取
- ✅ 基础统计分析功能
- ✅ 多维度切片分析
- ✅ 基础可视化图表
- ✅ HTML报告生成

### 计划中的功能
- [ ] 数据库连接支持
- [ ] 机器学习模型集成
- [ ] 交互式仪表板
- [ ] API接口开发
- [ ] 云端部署支持

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙋‍♂️ 联系方式

- 作者: fqz-boss
- GitHub: [@fqz-boss](https://github.com/fqz-boss)
- 项目链接: [https://github.com/fqz-boss/analyse_any_data](https://github.com/fqz-boss/analyse_any_data)

## 🌟 支持项目

如果这个项目对您有帮助，请给它一个 ⭐ Star！

---

<div align="center">
  <h3>📊 让数据分析变得简单高效！</h3>
  <p>Analyse Any Data - Your Smart Data Analysis Companion</p>
</div>
