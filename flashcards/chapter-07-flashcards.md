## Chapter 7: Domain 7: Deep Learning and Computer Vision Basics — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | What does a single perceptron compute? | output = f(Σ(w·x) + b) — weighted sum of inputs plus bias, passed through an activation function f. Exam tip: the perceptron is the basic building block of every layer in a neural network. |
| 2 | ReLU activation function formula and primary benefit? | f(x) = max(0, x). Benefit: avoids vanishing gradients in deep networks (unlike sigmoid/tanh). Exam tip: default choice for hidden layers in CNNs. |
| 3 | Sigmoid activation output range and best use case? | Outputs values between 0 and 1. Used for binary classification output layers. Exam tip: causes vanishing gradients if used in many hidden layers of a deep network. |
| 4 | Softmax activation — what does it produce and when is it used? | Converts a vector of raw scores (logits) into a probability distribution that sums to 1. Used on the output layer for single-label multi-class classification. Exam tip: pairs with cross-entropy loss. |
| 5 | Forward propagation vs. backward propagation — what's the difference? | Forward: input flows through layers to produce a prediction. Backward: gradients of the loss w.r.t. each weight are computed via the chain rule and used to update weights. Exam tip: backprop requires a differentiable loss function. |
| 6 | Gradient descent weight update rule? | w_new = w_old − (learning_rate × gradient). Exam tip: learning rate too high → loss diverges/oscillates; too low → very slow convergence. |
| 7 | What does a convolutional layer do in a CNN? | Slides learnable filters (kernels) across the input to detect local spatial patterns like edges and textures. Exam tip: output size depends on kernel size, stride, and padding. |
| 8 | What does a pooling layer (e.g., max pooling) do in a CNN? | Downsamples feature maps to reduce spatial dimensions, computation, and overfitting risk. Exam tip: pooling layers have no learnable weights. |
| 9 | Typical CNN architecture layer order? | Input → [Convolution → Activation (ReLU) → Pooling] repeated → Flatten → Fully Connected layer(s) → Output activation (Softmax/Sigmoid). Exam tip: FC layers always come after the conv/pooling feature-extraction blocks. |
| 10 | When should you use transfer learning instead of training from scratch? | When you have a small labeled dataset or limited compute budget. Reuse a pretrained network, freeze early (generic feature) layers, and fine-tune later (task-specific) layers. Exam tip: freezing early layers prevents overfitting on small datasets. |
| 11 | Standard loss function for multi-class classification? | Cross-entropy loss, paired with a softmax output layer. Exam tip: cross-entropy heavily penalizes confident but wrong predictions. |
| 12 | Core steps of a PyTorch training iteration, in order? | optimizer.zero_grad() → output = model(input) → loss = criterion(output, target) → loss.backward() → optimizer.step(). Exam tip: forgetting zero_grad() causes gradients to accumulate across batches. |
