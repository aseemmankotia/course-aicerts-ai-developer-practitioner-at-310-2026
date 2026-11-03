## Chapter 7: Domain 7: Deep Learning and Computer Vision Basics — Practice Questions

**Q1.** A model needs to classify an image into exactly one of 10 mutually exclusive categories. Which activation function should be used on the output layer?

A) Softmax
B) Sigmoid
C) ReLU
D) Tanh

<details>
<summary>Answer</summary>

**Correct: A**

Softmax converts raw output scores (logits) into a probability distribution across all classes that sums to 1, matching single-label multi-class classification.

**Why the others are wrong:**
- Sigmoid outputs an independent probability per neuron (0-1) and is used for binary or multi-label classification, not mutually exclusive multi-class.
- ReLU is used in hidden layers to introduce non-linearity; it does not produce a probability distribution and is unbounded.
- Tanh squashes values between -1 and 1 and is occasionally used in hidden layers, but does not produce a normalized probability distribution for classification output.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A CNN includes a max pooling layer after each convolutional block. What is the PRIMARY purpose of this pooling layer?

A) Reduce spatial dimensions of feature maps to lower computation and control overfitting
B) Learn additional filters to extract more complex features
C) Convert the 2D feature maps into a 1D vector for the output layer
D) Normalize pixel values before the next convolution

<details>
<summary>Answer</summary>

**Correct: A**

Pooling (e.g., max pooling) downsamples feature maps, reducing width and height, which decreases parameter count in later layers and provides translation invariance, helping control overfitting.

**Why the others are wrong:**
- Pooling layers have no learnable weights — filter learning happens in convolutional layers.
- Flattening 2D maps into a 1D vector is done by a Flatten layer before the fully connected layers, not pooling.
- Normalization is a separate operation (e.g., batch normalization), not the function of pooling.

</details>

---

**Q3.** During training of a 20-layer network using sigmoid activations in all hidden layers, the loss stops improving after a few epochs even though training accuracy is low. What is the MOST likely cause?

A) The learning rate is too high, causing the optimizer to overshoot the minimum
B) The batch size is too large for the dataset
C) Vanishing gradients caused by repeated sigmoid derivatives shrinking toward zero in deep layers
D) Softmax was used instead of cross-entropy loss

<details>
<summary>Answer</summary>

**Correct: C**

Sigmoid's derivative is at most 0.25 and approaches zero for large positive or negative inputs. In deep networks, the chain rule multiplies many small gradients together during backpropagation, causing gradients in early layers to vanish and stalling learning — this is why ReLU is preferred for hidden layers in deep networks.

**Why the others are wrong:**
- A too-high learning rate typically causes loss to oscillate or diverge, not plateau with low accuracy from the start.
- Batch size affects training stability and speed but is not the primary explanation for a depth-related stall tied specifically to sigmoid usage.
- Softmax is an activation function, not a loss function, and this distractor doesn't address the stated symptom tied to activation choice and depth.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A team has only 500 labeled images to train an image classifier and limited GPU budget. Which approach BEST meets these constraints while achieving good accuracy?

A) Use transfer learning: load a pretrained CNN, freeze early convolutional layers, and fine-tune only the later layers and classifier head
B) Train a new CNN from scratch with random weight initialization
C) Increase the dataset size by only using data augmentation, with no pretrained model
D) Train a fully connected network directly on raw pixel values without convolutional layers

<details>
<summary>Answer</summary>

**Correct: A**

Transfer learning reuses generic low-level features (edges, textures) learned on a large dataset, requiring far less labeled data and compute to adapt the model to a new task by fine-tuning only the later, task-specific layers.

**Why the others are wrong:**
- Training from scratch with only 500 images and limited compute typically leads to severe overfitting and poor generalization.
- Augmentation alone cannot substitute for the feature-learning benefit of a pretrained network and still requires significant compute to train from scratch.
- A fully connected network on raw pixels ignores spatial structure in images and performs far worse than a CNN-based approach for vision tasks.

</details>

---

**Q5.** In a basic perceptron, what does each weight represent?

A) The activation function applied to the output
B) The strength/importance of the connection between an input and the neuron's output
C) The learning rate used during gradient descent
D) The number of layers in the network

<details>
<summary>Answer</summary>

**Correct: B**

A weight scales how much a given input contributes to the neuron's weighted sum before the activation function is applied, representing the learned importance of that input.

**Why the others are wrong:**
- The activation function is a separate, fixed non-linear function applied after the weighted sum, not the weight itself.
- The learning rate is a hyperparameter controlling the size of weight updates during training, not the weight value.
- The number of layers is an architectural choice unrelated to what an individual weight represents.

</details>

---

**Q6.** During training, the loss decreases for the first few epochs, then suddenly spikes to a very large value and oscillates. Which configuration change is MOST likely to fix this?

A) Increase the number of convolutional layers
B) Switch the loss function from cross-entropy to mean squared error
C) Decrease the learning rate used by the optimizer
D) Remove all pooling layers from the network

<details>
<summary>Answer</summary>

**Correct: C**

A learning rate that is too high causes gradient descent to take overly large steps, overshooting minima and causing the loss to spike and oscillate instead of converging smoothly.

**Why the others are wrong:**
- Adding more convolutional layers increases model complexity but does not address an unstable optimization step size.
- Switching loss functions changes what is being optimized but does not directly fix oscillation caused by step size; MSE is also not standard for classification.
- Removing pooling layers affects feature map size and computation, not the stability of the gradient descent update step.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which sequence correctly describes the core steps inside a single PyTorch training iteration?

A) loss.backward() → optimizer.step() → model(input) → optimizer.zero_grad()
B) model(input) → optimizer.step() → loss.backward() → optimizer.zero_grad()
C) optimizer.zero_grad() → output = model(input) → loss = criterion(output, target) → loss.backward() → optimizer.step()
D) loss = criterion(output, target) → optimizer.zero_grad() → model(input) → loss.backward()

<details>
<summary>Answer</summary>

**Correct: C**

The standard PyTorch loop clears old gradients first (zero_grad), runs the forward pass, computes loss, backpropagates gradients (backward), then updates weights (step) — in that exact order.

**Why the others are wrong:**
- This order updates weights (step) before computing gradients (backward), which is logically invalid.
- This order calls optimizer.step() before gradients are even computed with backward(), which would have no effect or use stale gradients.
- This order computes loss before running the forward pass to get 'output', which is not possible since output doesn't exist yet.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the main difference between the convolutional layers and the fully connected (dense) layers in a CNN?

A) Convolutional layers have no learnable parameters, while fully connected layers do
B) Fully connected layers are only used for image data, while convolutional layers are used for text data
C) Convolutional layers can only be used once per network, while fully connected layers can be repeated many times
D) Convolutional layers apply local, shared filters across spatial regions to extract features, while fully connected layers connect every input neuron to every output neuron for final classification

<details>
<summary>Answer</summary>

**Correct: D**

Convolutional layers slide small shared-weight filters across the input to detect local spatial patterns efficiently, while fully connected layers at the end flatten these features and connect every neuron to every output for final classification decisions.

**Why the others are wrong:**
- Convolutional layers do have learnable parameters — the filter/kernel weights — contrary to this statement.
- This reverses typical usage: convolutional layers are standard for image data, not fully connected layers.
- Both convolutional and fully connected layers can be stacked multiple times in a network; there's no such restriction.

</details>

---

