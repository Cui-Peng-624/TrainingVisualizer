# TrainingVisualizer: A Tool for Visualizing the Deep Learning Training Process

## Project Overview

**TrainingVisualizer** is a tool designed to visualize the training process of deep learning models. It can dynamically plot the changes of various metrics (such as `loss`, `accuracy`, etc.) during both the training and testing phases. Additionally, it tracks and displays the highest `accuracy` and lowest `loss` during the training process, helping users identify the best performance of their model.

## Features

- Dynamically plots the curves of any metrics (e.g., `loss`, `accuracy`, etc.) during training and validation
- Automatically records the highest `accuracy` and lowest `loss` during training
- Supports custom configurations for chart title, legend, axis labels, etc.
- Compatible with any environment that supports plotting with `matplotlib`

> **Note**: Although `TrainingVisualizer` only records the highest `accuracy` and lowest `loss`, it can visualize the changes of any metrics, such as `precision`, `recall` on the validation set, or other custom metrics.

## Usage

### 1. Initialize `TrainingVisualizer`

```python
from visualization import TrainingVisualizer

# Initialize the visualizer
visualizer = TrainingVisualizer(
    xlabel='Epoch',
    ylabel='Value',
    title='Train Model',
    legend=['training_loss', 'training_acc', 'testing_loss', 'testing_acc']
)
```

### 2. Add data and update the chart during training

At the end of each epoch, use the `add` method to input the `epoch` number and corresponding metric data (such as `loss`, `accuracy`). The chart will update automatically.

```python
for epoch in range(num_epochs):
    train_acc, train_loss = # Results from model training
    val_acc, val_loss = # Results from model validation
    visualizer.add(epoch, [train_loss, train_acc, val_loss, val_acc])
```

### 3. Result display

In the chart, along with the plotting of any metrics (such as `loss` and `accuracy`), the highest `accuracy` and lowest `loss` during the training process will also be displayed.

## Project Structure

```
├── visualization.py          # Implementation of the visualization class
├── README.md                 # Project documentation
└── test_visualization.ipynb  # Test script
```

## Contribution

You are welcome to report issues, provide suggestions, or contribute to the code. Feel free to participate in this project by submitting an issue or a pull request.
