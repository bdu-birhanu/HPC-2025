# HPC: From Bare Metal to User Experience

## Understanding an On-Premises HPC Environment

High-Performance Computing (HPC) is often described in terms of CPUs, GPUs, compute nodes, storage, networking, and schedulers.

For an HPC user, the experience may appear simple:

```bash
sbatch my_job.sh
```

Behind that command is a complete platform of hardware, Linux, networking, storage, resource management, software environments, and user-facing services working together to run a workload.

This repository explores that journey:

> **From bare-metal infrastructure to the User experience.**

---

## The HPC Journey

The goal is to understand how the different layers of an HPC environment fit together:

```text
                    USER
                      |
                      v
               User Experience
                      |
                      v
              Applications / Jobs
                      |
                      v
               Slurm Scheduler
                      |
             +--------+--------+
             |                 |
          CPU Nodes         GPU Nodes
             |                 |
      Traditional HPC       AI / GPU
        Workloads          Workloads
             |                 |
             +--------+--------+
                      |
               Software Stack
                      |
              Storage / Network
                      |
                  Linux OS
                      |
                 Bare Metal
```

The focus is on a **single heterogeneous on-premises HPC platform** supporting both traditional CPU workloads and GPU/AI workloads.

---

## What This Repository Covers

### HPC Architecture

- Bare-metal infrastructure
- Provisioning
- CPU and GPU compute
- Linux system layer
- Networking
- Storage

### Workload Management

- Slurm
- Job lifecycle
- CPU workloads
- GPU workloads
- Resource requests
- Job scheduling

### Software Environment

- Environment Modules
- MPI
- CUDA
- Libraries
- Containers
- Scientific and AI software environments

### Troubleshooting

- Pending jobs
- Failed jobs
- Resource problems
- GPU visibility
- Storage and I/O issues
- Network problems
- Software environment issues

### User Experience

- From login to results
- Common HPC user problems
- HPC support workflows
- Documentation and training
- Bridging infrastructure and research applications

---

## Why This Project?

As a **Research Computing Facilitator**, I work at the intersection of HPC infrastructure and the people who use it.

Consulting HPC users requires more than knowing how to submit a job. It requires understanding how hardware, operating systems, schedulers, storage, networking, software, and applications interact.

This project is an effort to document and strengthen that systems-level understanding.

The central question is:

> **What actually happens between a user's first interaction with an HPC platform and the moment their application produces results?**

---

## About

I work in research computing and HPC user support, helping researchers, faculty, and students use HPC resources for computational research.

My work includes user support, software environments, workflow troubleshooting, documentation, training, and helping bridge the gap between HPC infrastructure and scientific applications.

This repository represents my ongoing learning and professional development in **HPC systems, infrastructure, operations, and user experience**.

---

## Important Note

Examples in this repository are intended for educational and professional-development purposes.

This repository will not contain:

- Credentials
- Internal IP addresses
- User information
- Proprietary configurations
- Confidential infrastructure details

---

## Project Status

**Work in progress...**

This repository will evolve as I continue learning, documenting, testing, and exploring different aspects of HPC infrastructure and research computing.

---

> **From bare metal to user experience — understanding the systems behind HPC.**
