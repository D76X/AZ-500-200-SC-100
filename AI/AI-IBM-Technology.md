# IBM Technology

[Spec-Driven Development: AI Assisted Coding Explained - IBM Technology](https://www.youtube.com/watch?v=mViFYTwWvcM)  

[AI in the SDLC: Rethinking AI Coding Tools & AI Agents IBM Technology and IBM Developer](https://www.youtube.com/watch?v=4wMRXmLpdA8)

---

[How KV Cache Speeds Up LLMs for Faster AI Models on GPUs IBM Technology and Red Hat](https://www.youtube.com/watch?v=o0gkdZBtwEg)  

[Goodbye Tokenmaxxing: From AI Usage to Agentic AI Outcomes IBM Technology and IBM Developer](https://www.youtube.com/watch?v=FheRqx7DjbU)  

---

# AI Foundamentals

[The AI Memory Wall: Why LLMs & AI Accelerators Hit a Bottleneck IBM Technology](https://www.youtube.com/watch?v=4b6KpFN7Rio)    

[AI Is Exposing Your Data: An AI Security Problem You Can't See](https://www.youtube.com/watch?v=kyJ1vd7yEPc)  

[AI Inference: The Secret to AI's Superpowers IBM Technology](https://www.youtube.com/watch?v=XtT5i0ZeHHE)  

[How AI Models Scale Beyond a Single GPU Across LLM Workloads IBM Technology](https://www.youtube.com/watch?v=qZBibWYcKH4)   

[Context Engineering for AI Agents: 4 Failure Modes to Avoid IBM Technology](https://www.youtube.com/watch?v=BwXremQ-i6I)   

[Prompt to Production: The Future of AI Code Workflows IBM Technology and IBM Developer](https://www.youtube.com/watch?v=bs1qPy_CWkM)   

[Agentic Engineering: 5 Terms Every AI Developer Should Know IBM Technology and IBM Developer](https://www.youtube.com/watch?v=SIZsFGvtClM)  

[What Is Loop Engineering? Building Better AI Agents IBM Technology](https://www.youtube.com/watch?v=DQBqh6gcx7U)   

[AI Model vs Agentic Harness: What Actually Drives AI IBM Technology](https://www.youtube.com/watch?v=ZELPNFXJ4_o)  

---

# Jev

[What Is Jev? The AI Model That Doesn't Generate Text IBM Technology](https://www.youtube.com/watch?v=YGgNBcIgI4s)  

[The Problem with Jev: Can You Trust AI Decisions? IBM Technology](https://www.youtube.com/watch?v=_yO_Q7qo0HQ&t=18s)    

---

# What is Arithmetic Intensity in AI?

Arithmetic intensity in AI is the ratio of floating-point operations (FLOPs) performed to the number of memory bytes transferred (read or written) during a computation: 

[1] (https://www.iguazio.com/glossary/arithmetic-intensity/), 
[2] (https://www.calibreos.com/decoder/arithmetic-intensity)
\(\text{Arithmetic\ Intensity}=\frac{\text{FLOPs}}{\text{Bytes\ Transferred}}\)

It measures how much math a chip does for every byte it moves from or to memory. 

[1] (https://inferencex.semianalysis.com/glossary/arithmetic-intensity),  
[2] (https://www.bohrium.com/en/sciencepedia/feynman/keyword/arithmetic_intensity)

Core Concepts

- `Compute-Bound` vs. `Memory-Bound`: 

Arithmetic intensity determines whether a neural network layer or kernel is limited by the speed of the processor or the speed of the memory.

- `Compute-Bound (High Intensity)`: 

The chip spends more time doing math than waiting for data. **Performance scales with peak FLOPS**. 

Operations like `large matrix multiplications (\(GEMM\))` and `convolutions` have high intensity.

- `Memory-Bound (Low Intensity)`: 

The processor sits idle, waiting for data to stream in from 
`High Bandwidth Memory (HBM) or DRAM`. 
**Performance scales with memory bandwidth, not raw compute**.

`Element-wise operations`, `normalizations`, and `small-batch inference decodes` have low intensity. 

[1] (https://arxiv.org/abs/2512.14090), 
[2] (https://ayoob.ai/blog/webgpu-matrix-multiplication-gemm-arithmetic-intensity), 
[3] (https://www.reddit.com/r/MachineLearning/comments/1lrc7vh/d_understanding_optimal_batch_size_calculation/), 
[4] (https://arxiv.org/html/2512.14090v2), 
[5] (https://inferencex.semianalysis.com/glossary/arithmetic-intensity), 
[6] (https://www.calibreos.com/decoder/arithmetic-intensity)

- `The Roofline Model`: 

Arithmetic intensity is plotted on the horizontal axis of a Roofline chart to visually show whether an algorithm hits a hardware's compute ceiling or its memory-bandwidth ceiling. 

[1] (https://modal.com/gpu-glossary/perf/arithmetic-intensity), 
[2] (https://arxiv.org/html/2512.14090v2)

- `Ridge Point`: 
The specific arithmetic intensity value where a piece of hardware transitions from being memory-bound to compute-bound. Modern AI accelerators require high intensity to saturate their tensor cores (e.g., around 156 FLOPs/byte for an NVIDIA A100 in BF16, ~295 for H100, and ~281 for B200). 

[1] (https://modal.com/gpu-glossary/perf/arithmetic-intensity)

## Why It Matters in AI & LLMs

- Prefill vs. Decode Phase:
	
    - Prefill: 
    Processes many prompt tokens simultaneously against a static set of weights. Each loaded weight byte is reused across many computations, resulting in high arithmetic intensity (usually compute-bound).

	- Decode: 
    Generates one token at a time. It must constantly reload model weights and Key-Value (KV) cache memory for very little math (an intensity near 2 FLOPs/byte), making it heavily memory-bandwidth bound. [1] (https://www.calibreos.com/decoder/arithmetic-intensity), [2] (https://inferencex.semianalysis.com/glossary/arithmetic-intensity)
• Batch Size and Data Reuse: Increasing the batch size amortizes the cost of loading model weights across more sequences, raising the arithmetic intensity and improving GPU utilization. [1] (https://www.reddit.com/r/MachineLearning/comments/1lrc7vh/d_understanding_optimal_batch_size_calculation/), [2] (https://inferencex.semianalysis.com/glossary/arithmetic-intensity)
• Optimization Strategies: Techniques like quantization (e.g., reducing precision from FP16 to INT8/INT4) or mixed-precision frameworks (such as Arithmetic-Intensity-Aware Quantization) aim to boost arithmetic intensity and bypass the "memory wall". [1] (https://docs.nvidia.com/deeplearning/performance/dl-performance-getting-started/index.html), [2] (https://arxiv.org/abs/2512.14090), [3] (https://www.bohrium.com/en/sciencepedia/feynman/keyword/arithmetic_intensity)

> Refs

[The AI Memory Wall: Why LLMs & AI Accelerators Hit a Bottleneck IBM Technology](https://www.youtube.com/watch?v=4b6KpFN7Rio)    

---

# What is The Memory Wall in AI?

The **"memory wall"** in AI refers to the performance bottleneck created by the widening gap between how fast processors (like GPUs and specialized AI accelerators) can compute data versus how fast memory systems can supply that data.

While processor computing power has scaled dramatically over the years, the speed, bandwidth, and latency of traditional memory (DRAM) have lagged far behind. In the era of modern AI, this disparity has turned into a critical roadblock.

---

## Why the Memory Wall Hits AI Hard

Modern artificial intelligence—especially Large Language Models (LLMs) with billions of parameters—relies on continuous, massive data movement.

* **The Data Movement Bottleneck:** Training and running inference on neural networks requires constantly fetching model weights, intermediate values (activations), and gradients from memory. Because data transfer takes longer than the actual mathematical operations, the processor's computing cores frequently sit idle, waiting for data to arrive.

* **Massive Energy Costs:** Moving data back and forth across physical components consumes a tremendous amount of power. A large portion of an AI accelerator's high energy consumption goes strictly toward data transit rather than active computation.

* **Inference Latency & Throughput:** For real-time, user-facing AI applications, the memory wall directly translates into slower token generation rates, lower system throughput, and higher latency.

---

## How the Industry is Fighting the Memory Wall

Engineers and hardware designers are utilizing several structural innovations to break through this barrier:

1. **High Bandwidth Memory (HBM):** Instead of standard distant RAM modules, modern AI hardware uses HBM—vertically stacked memory chips placed directly on the same silicon package as the processor. This dramatically widens the communication pathway (bus width) to drastically boost throughput.

2. **Compute-in-Memory (CiM):** Traditional computer architecture keeps processing and memory physically separate (the von Neumann bottleneck). CiM bypasses this by performing data processing directly inside or immediately adjacent to the memory array, minimizing transit distance and energy loss.

3. **Advanced Interconnects (e.g., CXL and Optical I/O):** Technologies like `Compute Express Link (CXL)` and emerging `optical interconnects` allow data centers to dynamically pool, scale, and accelerate memory access across large server clusters, easing the strain on individual GPUs.

> Refs

[The AI Memory Wall: Why LLMs & AI Accelerators Hit a Bottleneck IBM Technology](https://www.youtube.com/watch?v=4b6KpFN7Rio)    

---