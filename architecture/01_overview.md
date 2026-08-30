# HPC Architecture


An High-Performance Computing (HPC) environment is built as a combination of dedicated:
- Bare-metal hardware,
- Provisioning,
- High-performance compute resources,
- Linux-based system layer,
- Low-latency and high-throughput networking  and storage.

Where each layer plays an important role in delivering reliable and scalable compute performance.

## Bare-metal Infrastructure

Bare-metal servers form the foundation of the HPC environment. Unlike virtualized infrastructure, compute workloads run directly on physical hardware, providing predictable performance and direct access to CPU, memory, GPU, storage, and network resources.

### Provisioning & Cluster Management

Provisioning is responsible for bringing bare-metal HPC nodes from an unconfigured state to a production-ready cluster. This includes operating system deployment, firmware and driver configuration, network setup, and maintaining consistency across compute nodes.

**NVIDIA Base Command Manager (BCM)** formerly known as Bright Cluster Manager, is used to automate and manage cluster provisioning, providing centralized infrastructure management for compute nodes and supporting the deployment, configuration, monitoring, and lifecycle management of HPC and AI environments.

## CPU and GPU Compute

HPC workloads can use both CPU and GPU resources depending on their computational requirements. CPU nodes provide general-purpose parallel processing, while GPUs provide massive parallelism for workloads.

## Linux System Layer

Linux provides the core operating-system layer for most HPC environments. System administrators manage kernels, device drivers, filesystems, users, security, resource limits, and system services. The Linux layer also provides the foundation for compilers, libraries, MPI implementations, GPU software stacks, monitoring tools, and workload-management systems.

## Networking

High-performance networking is critical for communication between HPC nodes. Technologies such as InfiniBand and high-speed Ethernet provide the bandwidth and low latency required for distributed applications. Features such as RDMA allow applications to exchange data efficiently while reducing CPU overhead.

## Storage

HPC storage need to support large datasets and high levels of parallel I/O. The architecture may include local NVMe storage for high-speed temporary workloads, shared storage for persistent data, and parallel filesystems (e.g. GPFS) for large-scale workloads.


|   |
|:---|
 **The goal is not simply to build an HPC infrastructure.** The goal is to engineer an ecosystem where every layer works together, reliably, efficiently, and at scale, so that researchers and engineers can focus on solving the problems that matter. 

