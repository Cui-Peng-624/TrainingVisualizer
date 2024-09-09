# TrainingVisualizer: 深度学习训练过程可视化工具

## 项目简介

**TrainingVisualizer** 是一个用于深度学习模型训练过程的可视化工具，能够实时绘制训练和测试过程中任意标准（例如`loss`、`accuracy`等）的变化。此外，它还会记录并显示训练过程中最高的 `accuracy` 和最低的 `loss`，便于用户了解模型的最佳表现。

## 特性

- 实时绘制训练和验证过程中的任意标准（如`loss`、`accuracy`等）曲线
- 自动记录训练期间的最高 `accuracy` 和最低 `loss`
- 支持自定义图表标题、图例、坐标轴标签等配置
- 适用于任何使用 `matplotlib` 进行图形绘制的环境

> **注意**: 尽管 `TrainingVisualizer` 只能记录最高的 `accuracy` 和最低的 `loss`，但它可以可视化任意指标的变化，例如验证集上的 `precision`、`recall` 或者其他自定义标准。

## 使用方法

### 1. 初始化 `TrainingVisualizer`

```python
from visualization import TrainingVisualizer

# 初始化可视化工具
visualizer = TrainingVisualizer(
    xlabel='Epoch',
    ylabel='Value',
    title='Train Model',
    legend=['training_loss', 'training_acc', 'testing_loss', 'testing_acc']
)
```

### 2. 在训练过程中添加数据并更新图表

在训练每个 epoch 结束时，使用 `add` 方法添加 `epoch` 数和对应的指标数据（如`loss`、`accuracy`），图表将自动更新。

```python
for epoch in range(num_epochs):
    train_acc, train_loss = # 模型训练返回的结果
    val_acc, val_loss = # 模型验证返回的结果
    visualizer.add(epoch, [train_loss, train_acc, val_loss, val_acc])
```

### 3. 结果展示

在图表中，除了绘制任意标准的变化（如`loss`和`accuracy`），还会显示当前训练过程中的最高 `accuracy` 和最低 `loss`。

## 项目结构

```
├── visualization.py          # 可视化类的实现
├── README.md                 # 项目说明
└── test_visualization.ipynb  # 测试
```

## 贡献

欢迎大家提出问题、建议，或者贡献代码。您可以通过提交 issue 或 pull request 的方式参与到本项目中。