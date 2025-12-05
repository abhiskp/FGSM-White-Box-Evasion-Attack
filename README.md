This project demonstrates a critical vulnerability in modern Deep Neural Networks (DNNs): the lack of Adversarial Robustness. We implemented a White-Box Attack to subtly manipulate a complex image, forcing a state-of-the-art classifier to misclassify it with high confidence. 

Key Security & ML Concepts 
Model Integrity: The core security risk tested. We prove a model cannot be trusted when faced with adversarial input.
White-Box Attack: The attacker has full knowledge of the model's parameters ($\boldsymbol{\theta}$) and architecture.
FGSM (Fast Gradient Sign Method): An efficient, single-step attack that exploits the model's gradient for perturbation generation.
Adversarial Examples: Inputs that are imperceptible to humans but cause erroneous predictions in AI models.

The Attack Formula
The FGSM relies on calculating the gradient of the loss function $J$ with respect to the input image $\mathbf{x}$, then adding a small perturbation ($\epsilon$) in the direction that maximizes that loss.
