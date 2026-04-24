Self Pruning Network

1.INTRODUCTION

Modern neural networks are often large and computationally expensive. To reduce model size and improve efficiency, pruning is used to remove unimportant weights.In this case study, we design a self-pruning neural network that learns to remove its own weights during training, instead of after training.

2.OBJECTIVES

• Build a neural network for CIFAR-10 classification 
• Introduce learnable gates per weight 
• Use L1 regularization to enforce sparsity 
• Analyse accuracy vs sparsity trade-off  

3. METHODOLOGY 
3.1 Prunable Linear Layer
   Instead of standard nn.Linear, 
we create: y=(W⋅G)x+b Where: 
• (W): weights 
• (G): gates (0 to 1) 
Purpose of this Architecture: 
• nn.Parameter → makes weights & gates trainable 
• sigmoid → keeps gate values between 0 and 1 
• Multiplication → smoothly reduces weight importance 

3.2 Model Architecture 
• CIFAR-10 images → flattened 
• Fully connected network → simple baseline 
• ReLU → improves learning and sparsity  

3.3 Sparsity Loss
Usage of L1 Loss: 
• Encourages gates → 0 
• Leads to pruned connections  

4.TRAINING THE MODEL  
Combining Losses: 
• CE → improves accuracy 
• L1 → enforces pruning 
• λ → controls trade-off 

5. RESULTS - ACCURACY AND SPARSITY
Accuracy: 54.33%
Sparsity: 0.25%

6.CONCLUSION 

In this work, learnable gating mechanisms and L1 regularization were used to successfully create a self-pruning neural network. As evidenced by the diversity in gate values throughout the network, the model was able to understand the relative importance of links. The network did not completely remove less significant weights (hard pruning) under the specified training conditions, but it did lessen their strength (soft pruning), as seen by the observed sparsity remaining extremely low. This behaviour implies that gate values were not aggressively driven toward zero by the regularization strength and training length. Overall Stronger regularization, longer training, or different gating techniques could be future enhancements to achieve better results. 

