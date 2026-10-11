# Architectural Support for Mixture-of-Experts Models: GPUs, TPU Pods, and Dataflow Accelerators

## Abstract

Mixture-of-Experts (MoE) models grow their capacity by activating only a few experts for each token. This sparsity
moves the bottleneck from compute to the memory system and the interconnect. The expert weights are far larger than
on-chip memory, which experts a token needs is only known at run time, and spreading experts across devices requires
all-to-all communication at every MoE layer.

This project studies how three classes of hardware meet these demands: GPU clusters, TPU pods, and reconfigurable
dataflow accelerators with tiered memory. Drawing on recent ISCA and MICRO papers, it compares how each architecture
handles expert memory capacity, expert offloading and prefetching, and the communication pattern of expert
parallelism, and where each one falls short.

To ground the comparison, we will record real expert-routing traces from an open MoE model and use them to drive two
simulators. The first maps experts onto modeled interconnect topologies and measures load imbalance and all-to-all
traffic under random and topology-aware placement. The second models a two-tier memory and measures the expert cache
hit rate under LRU replacement and under prediction from the previous layer's routing. Based on these results, we
propose hardware-assisted expert prediction and topology-aware expert placement as directions for future AI
architectures.

## Author

Eshwari Khurd

## License

[MIT](LICENSE)
