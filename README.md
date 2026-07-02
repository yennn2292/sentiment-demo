# 教学视频评论情感分析系统 —— Web GUI Demo

实验五 任务三：文本情感分析与分类建模

## 运行方式

```bash
pip install flask snownlp jieba scikit-learn numpy
python3 app_web.py
```

启动后浏览器打开：http://127.0.0.1:5000

## 功能

- **实时批注**：输入一条评论，SnowNLP + KNN + 决策树 + 朴素贝叶斯 四个"阅卷人"实时给出判定，并给出综合投票结果
- **数据概览**：情感分布直方图、三种算法准确率对比（纯 SVG 绘制，无需联网）
- **批量批注**：一次粘贴多条评论，批量查看四方判定结果
- **关键词词云**：正/负面评论高频词对比
- **系统架构图**：数据层 → 情感分析层 → 特征工程层 → 模型层 → 应用层

## 文件结构

```
webapp/
├── app_web.py          # Flask 后端（模型训练 + API）
├── comments.csv         # 自建数据集（100条）
├── templates/
│   └── index.html       # 页面模板
└── static/
    ├── style.css         # 样式（Noto Serif/Sans SC + JetBrains Mono）
    ├── script.js         # 交互逻辑
    └── img/              # 词云图、架构图
```

## 说明

- 页面标题、正文字体通过 Google Fonts 在线加载（Noto Serif SC / Noto Sans SC / JetBrains Mono），
  无网络时会自动回退到系统自带字体，不影响功能。
- 统计图表全部使用原生 SVG 绘制，不依赖任何前端图表库，离线也能正常显示。
- 若 5000 端口被占用，可修改 `app_web.py` 最后一行的 `port=5000`。
