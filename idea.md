# Types of Attacks on Machine Learning Models and Their Defenses

## 1. Adversarial Attacks
Adversarial attacks involve creating small perturbations in input data that mislead the classifier.

### Example:
**Attack:**  
Fast Gradient Sign Method (FGSM) - Perturbs input images slightly along the gradient of the loss to fool the model.

### Defense:
- **Adversarial Training:** Augment training data with adversarial examples to make the model more robust.  
- **Gradient Masking:** Modify the loss gradients to make it harder for attackers to compute effective perturbations.  
- **Defensive Distillation:** Use a softer probability output during training to make the model less sensitive to small perturbations.

---

## 2. Poisoning Attacks
Poisoning attacks involve injecting malicious data into the training dataset to manipulate the model's predictions.

### Example:
**Attack:**  
Label flipping – flipping the labels of some training samples to confuse the model.

### Defense:
- **Data Sanitization:** Filter out anomalies in the training dataset using statistical techniques or outlier detection.  
- **Robust Learning Algorithms:** Use algorithms designed to handle noisy or maliciously labeled data.  
- **Differential Privacy:** Ensure that no single training example has a significant influence on the model.

---

## 3. Model Inversion Attacks
Model inversion attacks aim to reconstruct sensitive input data by exploiting model outputs.

### Example:
**Attack:**  
Query the model repeatedly with various inputs to approximate the original training data.

### Defense:
- **Output Regularization:** Limit the precision or confidence of the model's outputs to reduce information leakage.  
- **Secure Multiparty Computation (SMPC):** Implement cryptographic techniques to prevent adversaries from gaining insights through repeated queries.  
- **Differential Privacy:** Add noise to the output to obscure exact data patterns.

---

## 4. Evasion Attacks
Evasion attacks involve crafting inputs during testing or deployment to bypass a classifier.

### Example:
**Attack:**  
Adding subtle changes to an email to evade spam classifiers.

### Defense:
- **Feature Squeezing:** Reduce the degrees of freedom in the input, such as by rounding pixel values or reducing color depth in images.  
- **Ensemble Methods:** Use multiple classifiers and aggregate their results to make it harder for attackers to target all models simultaneously.  
- **Dynamic Detection:** Use runtime monitors to identify abnormal inputs or behaviors during deployment.

---

## 5. White-Box Attacks (Full Access)
The attacker has complete knowledge of the model, including architecture, parameters, and training data.

### Example:
**Attack:**  
Projected Gradient Descent (PGD) - Creates adversarial examples by iteratively perturbing input along the gradient of the loss function, utilizing full model knowledge.

### Defense Mechanisms:
- **Adversarial Training:** Incorporate adversarial examples during training to make the model robust.  
- **Gradient Masking:** Modify the model to produce misleading gradients, making it difficult for the attacker to generate effective perturbations.  
- **Randomized Smoothing:** Introduce random noise to inputs, ensuring predictions remain stable even under adversarial perturbations.

---

## 6. Black-Box Attacks (No Direct Access)
The attacker only observes the model’s outputs (e.g., predictions or probabilities) without access to internal details.

### Example:
**Attack:**  
Query-Based Attacks:  
Zeroth Order Optimization (ZOO) - Gradually estimate gradients using repeated queries to craft adversarial examples.

### Defense Mechanisms:
- **Output Obfuscation:** Round probabilities or provide only top-k predictions to reduce information leakage.  
- **Ensemble Models:** Use multiple models with diverse architectures to make attacks less effective.  
- **Rate Limiting:** Restrict the number of queries allowed within a given time frame to limit the attacker’s ability to probe the model.

---

## 7. Gray-Box Attacks (Partial Access)
The attacker has some knowledge of the model, such as the architecture or training data distribution, but lacks full access to parameters or gradients.

### Example:
**Attack:**  
Transfer-Based Attacks - Generate adversarial examples using a surrogate model trained on a similar dataset, assuming they transfer to the target model.

### Defense Mechanisms:
- **Input Transformation:** Preprocess inputs using techniques like JPEG compression, feature squeezing, or Gaussian noise to disrupt transferred adversarial patterns.  
- **Diverse Data Augmentation:** Train the model with variations of input data to minimize the effectiveness of transferred attacks.  
- **Randomized Defenses:** Apply random transformations (e.g., rotations, resizing) during inference to counteract adversarial input.

---

## 8. Insider Attacks (Privileged Access)
The attacker has insider knowledge, such as access to training data or the model's API, but no access to gradients.

### Example:
**Attack:**  
Data Poisoning - Inject malicious samples into the training data to compromise the model.

### Defense Mechanisms:
- **Data Validation and Sanitization:** Detect and remove anomalous or malicious data points before training.  
- **Robust Loss Functions:** Use loss functions designed to reduce the impact of poisoned samples, such as trimmed mean or Krum.  
- **Provenance Tracking:** Maintain logs of data collection and preprocessing to identify potential tampering.
