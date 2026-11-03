# Domain 7 Cheat Sheet: Deep Learning & Computer Vision Basics (9%)

## Neural Network Core Components
| Component | Role | Exam Note |
|---|---|---|
| Weight | Scales input importance | Learned during training |
| Bias | Shifts activation threshold | One per neuron |
| Activation function | Adds non-linearity | Without it, network = linear model |
| Layer | Group of neurons | Input → Hidden → Output |

## Activation Functions
| Function | Range | Typical Use | Exam Trap |
|---|---|---|---|
| Sigmoid | 0 to 1 | Binary output layer | Vanishing gradient in deep hidden layers |
| Tanh | -1 to 1 | Occasionally hidden layers | Still can vanish in very deep nets |
| ReLU | 0 to ∞ | Default hidden layer | "Dying ReLU" if inputs always negative |
| Softmax | 0 to 1, sums to 1 | Multi-class output | Confused with sigmoid for multi-label tasks |

## Forward vs Backward Propagation
- **Forward**: input → layers → prediction
- **Backward**: compute gradient of loss w.r.t. each weight via chain rule → update weights
- **Loss function**: measures prediction error (e.g., cross-entropy for classification, MSE for regression)
- **Gradient descent update**: `w = w - lr * gradient`
  - LR too high → diverges/oscillates
  - LR too low → slow convergence

## CNN Layer Types
| Layer | Purpose | Learnable Params? |
|---|---|---|
| Convolution | Extract local spatial features via filters | Yes |
| Pooling (max/avg) | Downsample, reduce computation & overfitting | No |
| Flatten | Convert 2D feature maps to 1D vector | No |
| Fully Connected (Dense) | Final classification/regression | Yes |

**Typical order:** Input → [Conv → ReLU → Pool] × N → Flatten → FC → Output activation

## Transfer Learning
| Scenario | Strategy |
|---|---|
| Small dataset, similar domain | Freeze most layers, fine-tune classifier head only |
| Larger dataset, similar domain | Freeze early layers, fine-tune later layers + head |
| Large dataset, different domain | Fine-tune entire network (use pretrained weights as init) |

**Why:** Early layers learn generic features (edges, colors); later layers learn task-specific features. Reusing a pretrained network drastically reduces data and compute needs.

## PyTorch Conceptual Workflow
```
1. Define model (nn.Module, layers in __init__, forward() method)
2. Define loss function (criterion)
3. Define optimizer (e.g., SGD, Adam)
4. Training loop per batch:
   optimizer.zero_grad()
   output = model(input)
   loss = criterion(output, target)
   loss.backward()
   optimizer.step()
```
**Common mistake:** Forgetting `zero_grad()` → gradients accumulate across batches, corrupting updates.

## Quick Memory Tricks
- **S**igmoid = **S**ingle probability (binary)
- **Soft**max = **Soft** (normalized) distribution across **many** classes
- **ReLU** = **Re**al fast, **L**inear for positives, zero otherwise
- Pooling = **shrink**, no learning; Convolution = **learn** features
