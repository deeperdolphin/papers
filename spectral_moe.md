# Spectral Mixture of Experts (Spectral MoE)

## Introduction

The Spectral Mixture of Experts (Spectral MoE) is a novel approach to enhance the expressiveness and adaptability of linear transformations in deep learning models. It builds upon the traditional nn.Linear layer by introducing a mixture of experts that are scaled components of the original linear transformation. The Spectral MoE module learns to selectively combine these scaled components based on the input, allowing for more flexible and expressive transformations.

## Motivation
In a traditional nn.Linear layer, the weight matrix can be decomposed using Singular Value Decomposition (SVD) into orthogonal matrices and a diagonal matrix containing the singular values. However, the linear transformation is often dominated by a few singular values, limiting its expressiveness. The Spectral MoE aims to address this limitation by introducing a mechanism to scale and mix the singular value components adaptively.

## Key Components
The Spectral MoE module consists of the following key components:

Original Linear Transformation: The module starts with a standard linear transformation using the weight matrix W.

Expert Scaling: The linear output is scaled by a set of learnable scaling parameters s. These scaling parameters adjust the importance or contribution of different singular value components of the original linear transformation.

Gating Mechanism: A gating mechanism is introduced to assign different weights to the scaled components (experts) based on the input. The gating mechanism determines the contribution of each expert to the final output, creating a mixture of experts.

Learnable Router: A learnable router is employed to adaptively balance the contributions of the averaged expert output and the original linear output. This allows the module to learn the optimal combination of the scaled components and the original linear transformation.

## Computational Formulation
The Spectral MoE module can be mathematically formulated as follows:

Original Linear Transformation: linear output = x * W

Expert Scaling: expert outputs = linear output * s

Gating Mechanism: gate output = sigmoid(linear output * G)

Applying Gate to Expert Outputs: gated expert outputs = expert outputs * gate output

Averaging Expert Outputs: averaged expert output = sum(gated expert outputs, axis=2) / gate count

Learnable Router: router output = sigmoid(x * R)

Combining Outputs: combined output = router output * averaged expert output + (1 - router output) * linear output
Where x is the input tensor, W is the weight matrix of the original linear transformation, s is the scaling parameters tensor, G is the gating transformation matrix, and R is the router transformation matrix.

## Benefits
The Spectral MoE offers several benefits over traditional linear transformations:

Expressiveness: By scaling and mixing the singular value components of the linear transformation, the Spectral MoE allows for more expressive and flexible transformations.
Adaptability: The gating mechanism and learnable router enable the module to adaptively combine the scaled components based on the input, leading to more adaptable and context-aware transformations.
Efficiency: The Spectral MoE introduces a small number of additional parameters (scaling parameters, gating transformation, and router transformation) compared to the original linear transformation, making it computationally efficient.

## Mathematical Definition as a Function of the SVD Decomposition:

The Spectral Mixture of Experts (Spectral MoE) is a novel approach that enhances the expressiveness and adaptability of linear transformations in deep learning models. It leverages the singular value decomposition (SVD) of the weight matrix in `nn.Linear` modules and introduces learnable scaling parameters, gating, and routing mechanisms to create a mixture of experts.

### SVD Decomposition

The weight matrix $W$ of an `nn.Linear` module can be decomposed using SVD as follows:

$$W = U \Sigma V^T$$

where $U$ and $V$ are orthogonal matrices, and $\Sigma$ is a diagonal matrix containing the singular values. The singular values represent the importance or strength of each component in the linear transformation.

### Spectral MoE Components

The Spectral MoE consists of several key components that build upon the SVD decomposition:

1. **Original Linear Transformation:**
   $$\text{linear output} = x W = x (U \Sigma V^T) = (x U) \Sigma V^T$$

2. **Expert Scaling:**
   $$\text{expert outputs} = \text{linear output} * s = ((x U) \Sigma V^T) * s = ((x U) (\Sigma * s)) V^T$$

3. **Gating Mechanism:**
   $$\text{gate output} = \sigma(\text{linear output} * G) = \sigma(((x U) \Sigma V^T) * G)$$

4. **Applying Gate to Expert Outputs:**
   $$\text{gated expert outputs} = \text{expert outputs} * \text{gate output}$$
   $$= (((x U) (\Sigma * s)) V^T) * \sigma(((x U) \Sigma V^T) * G)$$

5. **Averaging Expert Outputs:**
   $$\text{averaged expert output} = \frac{\sum(\text{gated expert outputs}, \text{axis}=2)}{\text{gate count}}$$

6. **Learnable Router:**
   $$\text{router output} = \sigma(x * R)$$

7. **Combining Outputs:**
   $$\text{combined output} = \text{router output} * \text{averaged expert output} + (1 - \text{router output}) * \text{linear output}$$

### Combined Output as a Function of SVD and Parameters

The combined output can be expressed as a function of the SVD decomposition and the scaling, routing, and gating parameters as follows:

$$\text{combined output} = \sigma(x * R) * \left(\frac{\sum((((x U) (\Sigma * s)) V^T) * \sigma(((x U) \Sigma V^T) * G)), \text{axis}=2)}{\text{gate count}}\right) + (1 - \sigma(x * R)) * ((x U) \Sigma V^T)$$

Here's how the combined output relates to the SVD decomposition and the parameters:
- The original linear transformation is represented by $(x U) \Sigma V^T$, which incorporates the SVD components $U$, $\Sigma$, and $V^T$.
- The expert scaling is applied to the singular values $\Sigma$ through element-wise multiplication with the scaling parameters $s$.
- The gating mechanism is applied to the linear output transformed by the gating parameters $G$, using the sigmoid activation function $\sigma$.
- The gated expert outputs are obtained by element-wise multiplication of the scaled expert outputs and the gate output.
- The averaged expert output is calculated by summing the gated expert outputs along `axis=2` and dividing by the `gate count`.
- The router output is obtained by applying the sigmoid activation function $\sigma$ to the input transformed by the routing parameters $R$.
- The combined output is a weighted sum of the averaged expert output and the original linear output, where the weights are determined by the router output.

By expressing the combined output in this way, we can see how the Spectral MoE leverages the SVD decomposition and learns to adapt the contributions of different experts through the scaling, gating, and routing mechanisms.
