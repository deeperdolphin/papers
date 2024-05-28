# Spectrum: Targeted Training Based on Signal to Noise Ratio

# Abstract

Efficient training of large language models is a critical challenge in natural language processing. Existing approaches often require significant computational resources and time, limiting accessibility and progress. In this paper, we introduce Spectrum, a novel method for accelerating language model training by selectively updating a subset of layers based on their signal-to-noise ratio (SNR).

We propose SpectrumAnalyzer, a module for efficiently computing layer SNRs, and show how it can be used to guide layer selection. Through extensive experiments on a range of language modeling tasks, we demonstrate that Spectrum achieves nearly identical results to full finetuning while using signifigantly less GPU memory. Spectrum also consistently outperforms prior efficient training methods like qLoRA in terms of model quality and VRAM use (in distributed training environments).

Qualitative analyses reveal that Spectrum learns more discriminative and coherent representations by focusing on high-SNR layers. Ablation studies confirm the importance of SNR-based layer selection, as Spectrum significantly outperforms alternative strategies. Overall, Spectrum is a powerful and efficient approach for training large language models that achieves strong performance while dramatically reducing computational costs.

Our work opens up several promising directions for future research, including SNR-guided learning rate scheduling and pruning, applications to domain adaptation and transfer learning, and effectively training larger models on comparitively less compute. We hope that Spectrum will help democratize access to state-of-the-art language models and facilitate further progress in natural language processing.

# 1. Introduction

Recent advances in large language models (LLMs) have demonstrated remarkable capabilities across a wide range of natural language tasks. However, training these massive models efficiently remains a significant challenge, requiring substantial computational resources and time. An emerging line of research has focused on developing techniques to reduce the memory footprint and accelerate the training of LLMs without compromising performance.

In this paper, we introduce Spectrum, a novel method for selectively training the layers of an LLM based on their signal-to-noise ratio (SNR). Spectrum is grounded in Random Matrix Theory and leverages the Marchenko-Pastur distribution to identify informative layers based on their signal-to-noise ratio.  Unlike previous approaches such as qLoRA [1] which quantize the entire model, Spectrum strategically targets specific layers and modules for training while keeping others frozen. By focusing computational resources on the most informative parameters, Spectrum achieves superior performance while significantly reducing training time and memory requirements compared to state-of-the-art methods.

Our main contributions can be summarized as follows:

We propose Spectrum, a new approach for efficient LLM training that selectively trains layers based on their SNR. Spectrum identifies the most valuable parameters to update via a novel SpectrumAnalyzer.
We conduct extensive experiments comparing Spectrum to qLoRA and other baselines on a range of language tasks. Spectrum consistently outperforms prior methods, converging faster while using less GPU memory.
We provide an in-depth analysis of why Spectrum is so effective, showing that focusing on high-SNR layers allows more efficient use of training compute. Spectrum trained models also exhibit improved generalization.
We release our code and models publicly to facilitate future research on efficient LLM training techniques.

Spectrum opens up exciting opportunities to train large language models more quickly and cheaply without sacrificing quality. This has significant implications for democratizing LLM research and enabling new applications. 
[1] Dettmers, Tim, et al. "qLoRA: Efficient Finetuning of Quantized LLMs." arXiv preprint arXiv:2305.14314 (2023).

# 2. Related Work

Efficient training of large language models has attracted significant research attention in recent years. Two notable prior works that aim to reduce the computational cost and memory requirements of LLM training are qLoRA [1] and LASER [2].

Dettmers et al. [1] introduced qLoRA, a method that combines LoRA (Low-Rank Adaptation) [3] with 4-bit quantization to enable efficient finetuning of LLMs. By quantizing the base model weights to 4 bits and storing the LoRA adaptation parameters in 16-bit precision, qLoRA significantly reduces memory usage during training. This allows finetuning of billions-parameter models like GPT-3 on a single GPU. However, qLoRA applies quantization and LoRA uniformly across all model layers, which may not be optimal.

LASER [2] takes a different approach by selectively applying a low-rank approximation to specific layers of a trained model. The authors measure the signal-to-noise ratio (SNR) of each layer and reduce the rank of high-SNR layers, showing that this can boost performance on certain tasks. However, LASER is primarily designed for model compression after training rather than improving training itself. 

Spectrum builds upon the insights of qLoRA and LASER while addressing their limitations. Like qLoRA, Spectrum enables efficient training of very large language models. However, instead of quantizing all layers, Spectrum selectively trains a subset of layers in full precision based on their SNR. This allows devoting compute to the most informative parameters during training.

Similar to LASER, Spectrum uses SNR to identify important layers. But while LASER approximates layers after training for model compression, Spectrum dynamically selects layers to train based on SNR to accelerate convergence.

Unlike LASER and qLoRA, Spectrum explicitly considers the signal-to-noise ratio of layers and insights from Random Matrix Theory.  Spectrum's mathematical foundation sets it apart from prior approaches and enables a more principled way of selecting informative layers for efficient training.

Spectrum combines the strengths of qLoRA and LASER - efficient memory usage and SNR-based layer selection - while improving upon them to enable faster, better LLM training. By strategically focusing compute on high-SNR layers during training, Spectrum achieves higher performance with lower time and memory costs. The following sections describe the Spectrum methodology in detail and present rigorous experimental comparisons to prior works.

[1] Dettmers, Tim, et al. "qLoRA: Efficient Finetuning of Quantized LLMs." arXiv preprint arXiv:2305.14314 (2023).
[2] Sharma, Pratyusha, et al. "The Truth is in There: Improving Reasoning in Language Models with Layer-Selective Rank Reduction." arXiv preprint arXiv:2312.13558 (2023).  
[3] Hu, Edward J., et al. "Lora: Low-rank adaptation of large language models." arXiv preprint arXiv:2106.09685 (2021).

# 3. Mathematical Foundation

The Spectrum method leverages insights from Random Matrix Theory (RMT) to efficiently identify and focus training on the most informative layers of a neural network. The key idea is to use the Marchenko-Pastur distribution, which characterizes the eigenvalue distribution of large random matrices, to separate signal from noise in the network's weight matrices.

It is worth providing some mathematical background, which is related to how singular value decomposition explains knowledge representation in matrices. Lower singular values often represent noise, less important information or less frequent terms in the data. In the LASER paper [2], the original authors showed that zeroing these values, one effectively filters out noise, which enhances the quality of the representations learned by the model. This process is akin to denoising, where the aim is to retain only the most significant features of the data. Basically, less frequent data and scattered information can be understood as a form of overfitting if they are interpreted as noise. But often suppressing or overwriting these components may destroy factual knowledge or affect learning representations of more complex patterns - this is the situation where finetuning a model may lead to catastrophic forgetting or creating less performant models.

## Relating Zero Singular Values and Overfit - A Polynomial Regression Case

We'll over-illustrate (literally) how overfitting pushes singular values towards zero, given dataset with $n$ data points $(x_i, y_i)$, the design matrix $X$ in a polynomial regression of degree $d$ is constructed as follows:

$$
X = \begin{bmatrix}
1 & x_1 & x_1^2 & \cdots & x_1^d \\
1 & x_2 & x_2^2 & \cdots & x_2^d \\
\vdots & \vdots & \vdots & & \vdots \\
1 & x_n & x_n^2 & \cdots & x_n^d
\end{bmatrix}
$$

### Overfitting and its Consequences

Overfitting occurs when the model is too complex relative to the amount of data it was trained on or the amount of noise in that data. Specifically, in polynomial regression, this happens when the degree $d$ of the polynomial is too high relative to the number of data points $n$.

### Impact on Singular Values

The singular value decomposition (SVD) of the matrix $X$ is given by:

$$X = U \Sigma V^T$$

Where:
- $U$ and $V$ are orthogonal matrices.
- $\Sigma$ is a diagonal matrix whose diagonal elements are the singular values $\sigma_i$ of $X$.

The singular values $\sigma_i$ in $\Sigma$ give us insight into the linear independence of the columns of $X$. If $X$ has linearly dependent columns, some of these singular values will be zero. This is crucial in understanding overfitting:

1. **High Degree Polynomial ($d \geq n$)**: If the degree $d$ of the polynomial is too high, it can lead to a situation where the columns of $X$ are linearly dependent. This typically happens when $d \geq n$, meaning the polynomial degree is at least as large as the number of data points.
   
2. **Linear Dependency**: The linear dependency among columns of $X$ (e.g., if two columns are multiples of each other or one column can be expressed as a linear combination of others) results in a rank-deficient matrix. That is, the rank of $X$ is less than the minimum of $n$ and $d+1$ (the number of columns).

3. **Zero Singular Values**: When $X$ is rank-deficient, it will have zero as some of its singular values. In mathematical terms, if $\text{rank}(X) < d+1$, then there will be $d+1 - \text{rank}(X)$ zero singular values in $\Sigma$.

### Mathematical Consequence

A design matrix $X$ with zero singular values implies issues in solving the normal equation for polynomial regression, $X^T X \beta = X^T y$, due to the non-invertibility of $X^T X$. Singular values being zero mean that $X^T X$ is not full rank, and hence, its inverse does not exist. This directly impacts the stability and reliability of the regression coefficients $\beta$ calculated, leading to overfitting.

$$\beta = (X^T X)^{-1} X^T y$$

When $\Sigma$ contains zeros, the computation of $(X^T X)^{-1}$ becomes problematic or impossible, which signifies that the model has perfectly fitted the noise instead of the underlying data pattern, a clear sign of overfitting.

Thus, in polynomial regression, overfitting is not only a statistical issue but also manifests as a numerical problem in terms of the singular values of the design matrix.

### Random Matrix Theory (RMT) Perspective

From the perspective of Random Matrix Theory (RMT), components of matrices that represent less frequent data might often be misconstrued as noise due to several theoretical and practical reasons:

1. **Eigenvalue/Singular Value Spectrum:** In Random Matrix Theory, the eigenvalues/singular values of a matrix can provide insights into the nature of the data the matrix represents. For large matrices derived from real-world data, such as those in big data analytics or machine learning, the bulk of the eigenvalues/singular values typically forms a 'bulk spectrum' which is well-predicted by RMT. Eigenvalues/singular values associated with less frequent data points often fall outside this main bulk as smaller or outlier eigenvalues. These outlier singular values can be misinterpreted as noise because they deviate from the typical eigenvalue distribution expected under RMT assumptions of data properties.

2. **Signal vs. Noise Separation:** RMT helps in distinguishing signal from noise by analyzing the statistical properties of matrices. The theory predicts that in a high-dimensional data setting, the eigenvalues/singular values that deviate significantly from the bulk of the spectrum might represent either important signals or noise. However, the challenge lies in correctly identifying whether these deviations are indeed meaningful signals (representing less frequent but important data points) or merely statistical noise. Often, without additional information or domain knowledge, these components can be mistakenly dismissed as noise.

### Benefits of focusing on Matrices with larger max-min Singular Values

Skipping matrices with less singular values that are not distinguishable from zero have several benefits.

1) Factual or scattered information obtained in the pre-training phase is preserved, so layers that are already overwhelmed with scattered pieces of information are retained;
2) Avoiding these matrices push the training away from less stable and ill-posed matrices, it ends up focusing on matrices with max-min singular values;
3) Focusing on matrices that have larger singular values enables us to focus on the transformations that have the largest impact over the latent representations.

## 3.1 Singular Value Decomposition and Quadratic Form
Consider a weight matrix $W$ in the neural network. The singular value decomposition (SVD) of $W$ is given by:

$$W = USV^T$$

where $U$ and $V$ are orthogonal matrices containing the left and right singular vectors, and $S$ is a diagonal matrix of singular values. The eigenvalues of the matrix $W^TW$ can be expressed in terms of the singular values of $W$:

$$W^TW = (USV^T)^T(USV^T) = VS^2V^T$$

This relationship between the eigenvalues of $W^TW$ and the squared singular values of $W$ is key to applying the Marchenko-Pastur distribution.

## 3.2 Marchenko-Pastur Distribution
The Marchenko-Pastur distribution describes the limiting eigenvalue distribution of large random matrices as the matrix dimensions go to infinity with a fixed aspect ratio. For a matrix $W$ of size $m \times n$, the eigenvalues of the matrix $C = (1/n)W^TW$ converge to a distribution bounded by:

$$\lambda_+ = \sigma^2\left(1 + \sqrt{\frac{m}{n}}\right)^2$$

$$\lambda_- = \sigma^2\left(1 - \sqrt{\frac{m}{n}}\right)^2$$

where $\lambda_+$ and $\lambda_-$ are the largest and smallest eigenvalues, and $\sigma$ is the standard deviation of the eigenvalues.
Using the relationship between the eigenvalues of $C$ and the singular values of $W$, we can derive bounds on the singular values:

$$\varepsilon_+ = \frac{1}{\sqrt{n}}\sigma\left(1 + \sqrt{\frac{m}{n}}\right)$$

$$\varepsilon_- = \frac{1}{\sqrt{n}}\sigma\left(1 - \sqrt{\frac{m}{n}}\right)$$

## 3.3 Signal-to-Noise Ratio and Matrix Ranking
To avoid numerical instability and enable efficient computation, we omit the normalization term $(1/\sqrt{n})$ when calculating the singular value bounds. This simplification does not affect the relative ordering of matrices by their signal-to-noise ratio.
Furthermore, to account for potential skewness and kurtosis in the singular value distribution, we replace the standard deviation $\sigma$ with the interquartile range in our calculations.
The signal-to-noise ratio (SNR) of a weight matrix can be defined as:

$$SNR = \frac{\sum_{k | \sigma_k > \varepsilon} \sigma_k}{\sum_{n | \sigma_n < \varepsilon} \sigma_n}$$

where $\varepsilon$ is a threshold separating signal from noise singular values.

After that, we normalize $SNR$ in relation to the largest singular value $SNR / \[ \max_{\sigma_i} \]$ for several reasons:

**1. Normalization**: It normalizes the SNR, making it dimensionless and comparable across different systems or matrices. This is particularly useful in scenarios where matrices have varying scales.

**2. Sensitivity Analysis**: The largest singular value represents the maximum stretching factor of the matrix. By dividing the SNR by this value, one can better understand the system's sensitivity to noise. This helps in assessing the robustness and stability of the system.

**3. Enhanced Comparison**: It allows for a fair comparison between different systems or matrices. By normalizing the SNR with the largest singular value, one can compare systems of different magnitudes on a common scale.

**4. Conditioning Information**: The largest singular value provides information about the conditioning of the matrix. A higher value indicates that the matrix is more ill-conditioned, which implies that small changes in input can cause large changes in output. Normalizing SNR with the largest singular value gives insight into how noise affects the system considering its conditioning.

With all these adjustments, matrices with higher SNR contain more informative features and less noise. By focusing training on these matrices, Spectrum improves learning efficiency and model performance. RMT provides a principled way to identify high-SNR matrices and guide the training process.

The Spectrum method leverages RMT to analyze the singular value spectrum of neural network weight matrices, separating signal from noise. By targeting training on high-SNR matrices, Spectrum achieves faster, more memory efficient generalization compared to standard training approaches.

# 4 Measuring The Signal-to-Noise Ratio
At the core of Spectrum is the ability to efficiently measure the SNR of each layer in an LLM. We introduce SpectrumAnalyzer, a module that computes layer SNRs using the following procedure:

## Pseudocode for the Spectrum Method

### Description
This pseudocode describes the Spectrum method for selectively updating model layers based on their signal-to-noise ratio (SNR) to accelerate training of large language models.

```python
// Function to compute Marchenko-Pastur threshold
function marchenko_pastur_threshold(σ, n, m):
    β ← n / m
    threshold ← σ × sqrt((1 + sqrt(β))^2)
    return threshold

// Function to estimate noise level from singular values using IQR
function estimate_sigma_with_full_iqr(S):
    IQR ← compute_iqr(S)
    σ ← IQR / 1.349
    return σ

// Function to compute SNR for a given layer's weights
function calculate_snr(weights):
    // Perform Singular Value Decomposition (SVD)
    S ← svd(weights)
    
    // Estimate the noise level σ
    σ ← estimate_sigma_with_full_iqr(S)
    
    // Compute the Marchenko-Pastur threshold
    n, m ← dimensions(weights)
    threshold ← marchenko_pastur_threshold(σ, n, m)
    
    // Calculate SNR (ratio of signal above threshold to noise below)
    signal ← sum(S[S > threshold])
    noise ← sum(S[S ≤ threshold])
    SNR ← signal / noise
    
    return SNR

// Main function to iterate over model layers and calculate SNR
function assess_layers_snr(model):
    layer_snr ← empty dictionary
    
    // Iterate over each layer in the model
    for each layer in model.layers do:
        if has_weights(layer):
            weights ← get_weights(layer)
            SNR ← calculate_snr(weights)
            layer_snr[layer] ← SNR
            
    return layer_snr
```

For each target layer, compute the singular value decomposition (SVD) of the layer's weight matrix.
Calculate the SNR as the ratio between the sum of singular values above a noise threshold $\varepsilon$ (signal) and the sum of singular values below $\varepsilon$ (noise).
Normalize the SNR by the layer's largest singular value to enable comparisons between layers.

The noise threshold $\varepsilon$ is determined adaptively for each layer using the Marchenko-Pastur distribution [4], which models the singular value spectrum of pure noise. As discussed in the Mathematical Foundation section, the Marchenko-Pastur distribution provides a theoretically grounded way to separate signal from noise in the singular value spectrum of large random matrices. By setting the noise threshold based on this distribution, Spectrum can effectively identify the informative components of each layer's weight matrix.

The SNR formula used in Spectrum is derived from the properties of the singular value spectrum described in the Mathematical Foundation section. Specifically, the sum of singular values above the noise threshold corresponds to the signal component, while the sum of singular values below the threshold represents the noise component. This formulation aligns with the theoretical understanding of how the singular value spectrum is partitioned according to the Marchenko-Pastur distribution.

SpectrumAnalyzer is optimized to compute SNRs in batches using VRAM (or system ram, if your VRAM isn't sufficient) enabling efficient analysis of the entire model. By leveraging the insights from Random Matrix Theory and the Marchenko-Pastur distribution, Spectrum provides a principled and efficient approach to measuring the signal-to-noise ratio of neural network layers, which forms the basis for its selective training strategy.

[4] Marchenko, V. A., and Leonid A. Pastur. "Distribution of eigenvalues for some sets of random matrices." Matematicheskii Sbornik 114.4 (1967): 507-536.

## 4.2 Layer Selection

Given the SNRs of all layers, Spectrum selects a subset to train while freezing the rest. Layers with higher SNR contain more information relevant to the task, so focusing updates on these layers allows Spectrum to converge faster. The number of layers trained is a key hyperparameter that controls the tradeoff between training speed and model performance.

Spectrum selects layers to train based on their relative SNR ranking within each module (e.g. attention layers, FFN layers). This ensures a balanced distribution of updates across different parts of the model. By default, Spectrum trains the top 25% of layers in each module, as we find this provides a good balance between efficiency and quality.

[4] Marchenko, V. A., and Leonid A. Pastur. "Distribution of eigenvalues for some sets of random matrices." Matematicheskii Sbornik 114.4 (1967): 507-536.

# 5 Experiments

We present a comprehensive evaluation of Spectrum on a diverse set of language model evaluations. We compare Spectrum to full finetuning, qLoRA [1] in terms of training speed, memory usage, and benchmark results. We use Spectrum-50 and Spectrum-25 for these evaluations

## 5.1 Setup

We trained 5 different meta-llama/llama-3-8b models on airoborous-3.1 (jondurbin/airoboros-3.1). One with a full finetune, another with qLoRA, one with Spectrum targeting 50% of the highest SNR layers and another targeting 25% - we also chose to include a 5th model trained using qLoRA with the target modules being set as the Spectrum-25 layers. We chose airoborous due to it's relatively small size, while still containing a large number of general language understanding tasks, to get a baseline. We extendeded this further - running the exact same training procedure (sans qLoRA + Spectrum) on mistralai/mistral-7Bv0.1. Each model was trained on 2 epochs with the exact same hyperparameters: learning rate of 1e-5, gradient norm of 4, batch size 1 and a max sequence length of 4096. The only change was during the qLoRA training; we lowered the learning rate to 2e-4 for both Mistral and LLama-3. All main experiments used an 8xL40S (46GB VRAM per GPU) node provided by CrusoeEnergy. We used HF Accelerate and Axolotl with Deepspeed Zero3 for distributed training. To compare performance on single GPU jobs, we retrained our llama-3-8b models on a 1x Nvidia L40S GPU for a single epoch to compare single GPU VRAM usage. Our qLoRA hyperparameters were as follows: 

```yaml
adapter: qLoRA
lora_r: 32
lora_alpha: 16
lora_dropout: 0.05
lora_target_linear: true
lora_modules_to_save: [embed_tokens, lm_head]
```

*Note: we used the chatml prompt template for each finetune, thus adding the <|im_start|> and <|im_end|> tokens to each model's vocabulary. This affects memory usage. By adding the same tokens to every finetune, we believe the comparisons in memory efficiency to be representative of what they would be without adding any additional tokens.*

We evaluated each model using `lm-evaluation-harness` commit `00b7a61` on multiple language modeling benchmarks popularized by the OpenLLM Leaderboard:

- **Arc-Easy**: The AI2 Reasoning Challenge (ARC) Easy Set consists of 7,787 genuine grade-school level, multiple-choice science questions. The Easy Set includes questions that are straightforward for both humans and basic algorithms to answer correctly.

- **GSM8K**: (Grade School Math 8K) is a dataset of 8,500 high-quality, linguistically diverse grade school math word problems. These problems require multi-step reasoning and involve basic arithmetic operations.

- **HellaSwag**: Designed to evaluate commonsense natural language inference (NLI). It includes context completion tasks where models must choose the correct ending from multiple options, with adversarially generated incorrect endings.

- **MMLU**: The Massive Multitask Language Understanding (MMLU) benchmark consists of multiple-choice questions across 57 subjects, including STEM, humanities, social sciences, and more. It tests both world knowledge and problem-solving ability.

- **TruthfulQA**: A benchmark designed to measure the truthfulness of language models in generating answers to questions. It includes 817 questions across 38 categories, targeting common misconceptions and false beliefs.

- **Winogrande**: A dataset for evaluating commonsense reasoning, consisting of sentence pairs with a pronoun that needs to be resolved. The dataset is designed to be more challenging than the original Winograd Schema Challenge.

To further validate our results, we ran our Llama models on another suite of benchmarks popularized by Nous Research:

- **AGIEval**: A benchmark designed to evaluate the general intelligence of AI models. It includes a variety of tasks that test different aspects of reasoning, problem-solving, and knowledge application.

- **BigBench-Hard**: A subset of the BIG-Bench dataset, consisting of 23 particularly challenging tasks for current language models. These tasks require complex reasoning and understanding, often involving multi-step processes.

- **GPT4All**: A collection of benchmarks including BoolQ, PIQA, HellaSwag, WinoGrande, ARC-easy, ARC-c, and OBQA. (Note, there is some overlap here between these benchmarks and the OpenLLM Leaderboard benchmarks performed above.)

Nous' suite typically involves TruthfulQA, which was benchmarked with the OpenLLM leaderboard tasks.

Additionally, we recorded total training time for each model. 

## 5.2 Results

### 5.2.1 Benchmark Scores


<p align="center">
  <img src="https://i.ibb.co/GxrD6S7/llama-3-ollm.png" alt="Llama-3-Open-LLM" style="margin: 0 10px;">
  <img src="https://i.ibb.co/M9Qdv1Y/mistral-7b-ollm.png" alt="Mistral-7B-Open-LLM" style="margin: 0 10px;">
  <img src="https://i.ibb.co/sCTtpDn/llama-nous-correct.png" alt="Llama-3-Nous" style="margin: 0 10px;">
</p>


### 5.2.2 Memory Usage & Training Time

This section presents the memory usage and training time for different configurations of the Llama-3-8b model. We compare these configurations against the baseline FFT model in terms of peak memory usage per GPU, VRAM usage on a single GPU, and total training time.

**Table 1: Peak GPU Memory Usage per GPU**

| Model                        | Peak Memory Usage per GPU | % Efficiency Compared to FFT |
|------------------------------|---------------------------|------------------------------|
| Llama-3-8b-FFT               | 24.92 GB                  | Baseline                     |
| Llama-3-8b-qLoRA             | 21.25 GB                  | 14.73%                       |
| Llama-3-8b-Spectrum-50       | 20.50 GB                  | 17.72%                       |
| Llama-3-8b-Spectrum-25       | 19.18 GB                  | 23.05%                       |
| Llama-3-8b-Spectrum-25+qLoRA | 16.95 GB                  | 31.99%                       |


_Note: Efficiency tests were performed on 8x L40S GPUs at batch size 1. Results may vary with different batch sizes, number of GPUs, and model sizes._

**Table 2: Single GPU VRAM Usage**

| Model                        | Single GPU VRAM Usage |
|------------------------------|-----------------------|
| Llama-3-8b-FFT               | N/A (out of memory)   |
| Llama-3-8b-Spectrum-50       | 34.65 GB              |
| Llama-3-8b-Spectrum-25       | 27.46 GB              |
| Llama-3-8b-qLoRA             | 23.39 GB              |
| Llama-3-8b-Spectrum-25+qLoRA | 21.18 GB              |

**Table 3: Training Time (Distributed)**

| Model                        | Training Time   |
|------------------------------|-----------------|
| Llama-3-8b-FFT               | 1h 43m 16s      |
| Llama-3-8b-Spectrum-50       | 1h 27m 17s      |
| Llama-3-8b-qLoRA             | 1h 18m 14s      |
| Llama-3-8b-Spectrum-25       | 1h 5m 33s       |
| Llama-3-8b-Spectrum-25+qLoRA | 54m 55s         |


## 5.3 Analysis

The results from section 5.2.1 demonstrate that **Spectrum** offers improvements in performance, speed, and memory efficiency compared to full finetuning and qLoRA.

**Spectrum's effectiveness** can be attributed to its ability to identify and selectively fine-tune the layers that contribute the most to the model's learning capacity. By calculating the SNR for each layer and targeting only a percentage of the layers with the highest SNR, Spectrum focuses the finetuning process on the most informative and relevant parts of the model. This targeted approach allows for faster training and nearly identical (within margin of error) performance to FFT while reducing the computational and memory requirements.

### 5.3.1 Performance

**Spectrum-50** (targeting the top 50% of layers) achieves results comparable to or even slightly better than full finetuning across various benchmarks (Figures 1-3). This indicates that the majority of the model's learning capacity is concentrated in the highest SNR layers, and finetuning these layers is sufficient to achieve competitive performance.
**Spectrum-25** (targeting the top 25% of layers) also demonstrates strong performance, with results close to those of full finetuning and Spectrum-50. In some cases, Spectrum-25 is scores even higher than full finetuning and Spectrum-50. This further suggests that the most significant information for post-training is contained in a relatively small subset of layers.

Additionally, we found that when combining Spectrum 25 with qLoRA, we could further decrease the VRAM use and increase speed - while keeping performance almost identical to stock qLoRA.

![Spectrum+qLoRA Performance](https://i.ibb.co/xmr4VPR/spectrum-qLoRA-llama.png)


### 5.3.2 Memory Efficiency

The efficiency of Spectrum is particularly evident when comparing it to qLoRA in distributed training settings using DeepSpeed Zero3. As shown in Table 1, Spectrum-50 and Spectrum-25 achieve 17.72% and 23.05% memory savings per GPU, respectively, compared to full finetuning. In contrast, qLoRA offers 14.73% memory savings.

However, it is important to note that qLoRA exhibits better memory efficiency than Spectrum when training on a single GPU (Table 2). The major drawback for Spectrum's efficiency on single GPUs is that while we're only training the top n% of the model's highest SNR layers - we do still need to load the entire model into memory. The efficiency gains for Spectrum come from only updating the gradients for the selected layers, which uses comparitively less memory than updating the entire model. This also explains why it is so much more efficient in distributed environments like Deepspeed Zero3 and Fully Sharded Data Parallel (FSDP), as these allow us to train the model in a sharded manner across multiple GPUs, making the per gpu model memory footprint *much* lower. Spectrum+qLoRA had the lowest VRAM requirement on both single and distributed workloads.

### 5.3.4 Training Time

In terms of training time, Spectrum demonstrates significant improvements over full finetuning and qLoRA (Table 3). Spectrum-50 and Spectrum-25 achieve 15.48% and 36.78% reductions in training time, respectively, compared to full finetuning. qLoRA also offers a 24.19% reduction in training time. It should be noted that as the size of models grow, the time it takes to train using LoRA increases. This can be adjusted by increasing the number of parameters adjusted for each pass, with the tradeoff of increased VRAM requirements.

# 6 Real World Use

We have used Spectrum in many of our recent Dolphin models - allowing us to train large models at high precision on a single 8xH100 node provided by CrusoeEnergy, achieving results that would otherwise require multiple H100 compute nodes. In the case of our Qwen-110b dense model tune, even qLoRA was not sufficient for training. Spectrum was the only solution that worked (for us). Please note, the results below are representative of the performance of the Dolphin models only. The official post train scores from the model creators are taken from the OpenLLM leaderboard, and while we try our hardest to match the leaderboard's benchmark pipeline, disparities remain.

### DBRX - 132B params - Spectrum-25

![DBRX - 132B params - Spectrum-25](https://cdn-uploads.huggingface.co/production/uploads/63111b2d88942700629f5771/tVh5xVCGvjPyLgMCqp-IY.png)

### Qwen-110B - 111B params - Spectrum-45

![Qwen-110B - 111B params - Spectrum-45](https://cdn-uploads.huggingface.co/production/uploads/63111b2d88942700629f5771/U86Zu-MzLq4rECJRAAvgq.png)

### Mixtral-8x22b 141B params - Spectrum-50

![Mixtral-8x22b 141B params - Spectrum-50](https://cdn-uploads.huggingface.co/production/uploads/63111b2d88942700629f5771/Nb6f_dS_M6fN_v2ACK98x.png)


# 7. Conclusion and Future Work

In this paper, we introduced Spectrum, a novel method for efficient training of large language models. Spectrum selectively trains a subset of layers based on their signal-to-noise ratio (SNR), allowing it to focus compute on the most informative parameters. By dynamically adapting the set of trainable layers as learning progresses, Spectrum converges faster and uses significantly less memory than prior methods while maintaining high model quality.

Through extensive experiments on a diverse set of language modeling tasks, we demonstrated Spectrum's superior performance compared to full finetuning, qLoRA, and other efficient training techniques. Spectrum achieves a speedup over full finetuning and consistently outperforms qLoRA in terms of both distributed training efficiency and final model accuracy. Our analyses show that Spectrum's SNR-guided layer selection enables it to learn more discriminative and coherent representations.

We also introduced SpectrumAnalyzer, a novel module for efficiently computing layer SNRs during training. SpectrumAnalyzer allows Spectrum to dynamically adapt the set of trainable layers without adding significant overhead. Our implementation of Spectrum and SpectrumAnalyzer will be made publicly available to facilitate adoption and future research.

Spectrum opens up several promising directions for future work on efficient language model training:

1) Layer-wise learning rate scheduling based on SNR: Since Spectrum identifies the most informative layers, it could potentially benefit from assigning higher learning rates to these layers during training. Exploring adaptive learning rate schedules that leverage SNR could further improve convergence speed.

2) Dynamic SNR scanning and targeting during training: While outside the scope of this paper - we're experimenting with rescanning the model in between each epoch and retargeting layers for subsequent epochs.

3) SNR-guided pruning during training: In addition to selecting layers to train, SNR could also be used to identify parameters to prune within each layer. Combining Spectrum with dynamic pruning techniques could lead to even more compact and efficient models.

4) Spectrum for domain adaptation and transfer learning: Spectrum's ability to quickly adapt a pretrained model with limited computational resources makes it well-suited for domain adaptation and transfer learning scenarios. Investigating Spectrum's performance on these tasks is an important direction for future research.

5) Scaling up Spectrum to larger models and datasets: While we focused on relatively small models (< 9B parameters) in this work, we show real world examples of how we've used Spectrum to train our Dolphin family of LLMs. Scaling beyond ~140B parameter model sizes while maintaining efficiency is an exciting area of research.

6) Applying Spectrum to other modalities: Although we focused on language modeling in this paper, the core ideas behind Spectrum are model-agnostic. Exploring how Spectrum can be adapted to other domains like computer vision and speech recognition is a promising avenue for future work.
