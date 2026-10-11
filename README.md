# Architectural Support for Mixture-of-Experts Models: GPUs, TPU Pods, and Dataflow Accelerators

## Abstract

Mixture-of-Experts (MoE) models grow their capacity by activating only a few experts for each token. This sparsity
moves the bottleneck from compute to the memory system and the interconnect. The expert weights are far larger than
on-chip memory, which experts a token needs is only known at run time, and spreading experts across devices requires
all-to-all communication at every MoE layer.

This project studies how three classes of hardware meet these demands: GPU clusters, TPU pods, and reconfigurable
dataflow accelerators with tiered memory. Drawing on recent architecture and systems papers (ISCA, MICRO and SIGCOMM), it compares how each architecture
handles expert memory capacity, expert offloading and prefetching, and the communication pattern of expert
parallelism, and where each one falls short.

To ground the comparison, the project records real expert-routing traces from an open MoE model and uses them to drive
two simulators. The first maps experts onto modeled interconnect topologies and measures load imbalance and all-to-all
traffic under random and topology-aware placement. The second models a two-tier memory and measures the expert cache
hit rate under LRU replacement and under prediction from the previous layer's routing. Based on these results, it
proposes hardware-assisted expert prediction and topology-aware expert placement as directions for future AI
architectures.

## Papers

**Scale-out and interconnect:** how MoE stresses GPU clusters, TPU pods and the network

1. Zhao et al., "Insights into DeepSeek-V3: Scaling Challenges and Reflections on Hardware for AI Architectures," ISCA 2025. [DBLP](https://dblp.org/search?q=Insights+into+DeepSeek-V3+Scaling+Challenges+Reflections+on+Hardware+for+AI+Architectures)
2. Jouppi et al., "TPU v4: An Optically Reconfigurable Supercomputer for Machine Learning with Hardware Support for Embeddings," ISCA 2023. [DBLP](https://dblp.org/search?q=TPU+v4+Optically+Reconfigurable+Supercomputer+Machine+Learning+Hardware+Support+Embeddings)
3. Liao et al., "MixNet: A Runtime Reconfigurable Optical-Electrical Fabric for Distributed Mixture-of-Experts Training," SIGCOMM 2025. [DBLP](https://dblp.org/search?q=MixNet+Runtime+Reconfigurable+Optical-Electrical+Fabric+Distributed+Mixture-of-Experts+Training)

**Memory and new hardware:** how chips store, move and predict experts

4. Prabhakar et al., "SambaNova SN40L: Scaling the AI Memory Wall with Dataflow and Composition of Experts," MICRO 2024. [DBLP](https://dblp.org/search?q=SambaNova+SN40L+Scaling+the+AI+Memory+Wall+Dataflow+Composition+of+Experts)
5. Hwang et al., "Pre-gated MoE: An Algorithm-System Co-Design for Fast and Scalable Mixture-of-Expert Inference," ISCA 2024. [DBLP](https://dblp.org/search?q=Pre-gated+MoE+Algorithm-System+Co-Design+Fast+Scalable+Mixture-of-Expert+Inference)
6. Yun et al., "Duplex: A Device for Large Language Models with Mixture of Experts, Grouped Query Attention, and Continuous Batching," venue to be confirmed. [DBLP](https://dblp.org/search?q=Duplex+Device+Large+Language+Models+Mixture+of+Experts+Grouped+Query+Attention+Continuous+Batching)

Full references are exported from DBLP.

## Author

Eshwari Khurd

## License

[MIT](LICENSE)
