This project demonstrates a critical vulnerability in modern Deep Neural Networks (DNNs): the lack of Adversarial Robustness. We implemented a White-Box Attack to subtly manipulate a complex image, forcing a state-of-the-art classifier to misclassify it with high confidence. 

Key Security & ML Concepts 
Model Integrity: The core security risk tested. We prove a model cannot be trusted when faced with adversarial input.
White-Box Attack: The attacker has full knowledge of the model's parameters ($\boldsymbol{\theta}$) and architecture.
FGSM (Fast Gradient Sign Method): An efficient, single-step attack that exploits the model's gradient for perturbation generation.
Adversarial Examples: Inputs that are imperceptible to humans but cause erroneous predictions in AI models.

The Attack Formula
The FGSM relies on calculating the gradient of the loss function $J$ with respect to the input image $\mathbf{x}$, then adding a small perturbation ($\epsilon$) in the direction that maximizes that loss.

This project demonstrates a critical vulnerability in modern Deep Neural Networks (DNNs): the lack of Adversarial Robustness. We implemented a White-Box Attack to subtly manipulate a complex image, forcing a state-of-the-art classifier to misclassify it with high confidence.

🔑 Key Security & ML Concepts

- Model Integrity: The core security risk tested. We prove a model cannot be trusted when faced with adversarial input.

- White-Box Attack: The attacker has full knowledge of the model's parameters ($\boldsymbol{\theta}$) and architecture.

- FGSM (Fast Gradient Sign Method): An efficient, single-step attack that exploits the model's gradient for perturbation generation.

- Adversarial Examples: Inputs that are imperceptible to humans but cause erroneous predictions in AI models.

🔬 The Attack Formula

The FGSM relies on calculating the gradient of the loss function $J$ with respect to the input image $\mathbf{x}$, then adding a small perturbation ($\epsilon$) in the direction that maximizes that loss.

$$\mathbf{x}_{adv} = \mathbf{x} + \epsilon \cdot \text{sign}(\nabla_{\mathbf{x}} J(\boldsymbol{\theta}, \mathbf{x}, y))$$

Attack Parameters

| Parameter | Value | Role in Attack |
| :------------------------------------- | :------------------------------------- | :--------------------------------------------------------- |
| Victim Model ($\boldsymbol{\theta}$) | MobileNetV2 (Pre-trained on ImageNet) | The complex, deployed model we aim to break. |
| Perturbation Budget ($\epsilon$) | $0.05$ | Maximum allowed pixel change (controls noise visibility). |
| Input $\mathbf{x}$ | Labrador Retriever Image | The benign, correctly classified starting point. |



📊 Results: Successful Misclassification

The model was successfully fooled by the adversarial noise, despite the image remaining visually identical to the human eye.

| Metric | Baseline Class | Attack Target | Confidence Change |
| :--- | :--- | :--- | :--- |
| Input Image | Labrador Retriever | Saluki | — |
| Confidence | $41.39\%$ | $14.51\%$ | $-26.88\%$ |

Visualization


![FGSM Attack Visualization showing the original image, the noise (delta), and the resulting adversarial image misclassified by MobileNetV2.](source/fgsm_attack_result.png)


🛡️ Security Implication

The attack succeeded despite the clean image having only $41.39\%$ confidence because the small, gradient-aligned perturbation was enough to push the model's decision boundary into a different, incorrect class (Saluki).

This project proves the vital necessity for Adversarial Training and continuous Model Robustness Testing in any AI system used for security-critical tasks (e.g., threat detection, autonomous vehicles).

$$\text{NEXT STEP: Project 2 (Data Poisoning)}$$

This project will transition from attacking deployed models to compromising the ML supply chain (SecMLOps).
