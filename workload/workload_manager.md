# HPC Workload Management

Once the underlying HPC infrastructure is [provisioned](../architecture/01_overview.md#provisioning--cluster-management), the next step is managing how users and applications access the available compute resources.

As HPC clusters are shared environments, multiple users may submit jobs that compete for CPUs, memory, GPUs, storage, and other resources.

Workload management provides the mechanism for accepting these requests, allocating resources, scheduling workloads, monitoring execution, and managing jobs throughout their lifecycle.

In many HPC environments, Slurm serves as the workload management and job scheduling layer. So, this topic focuses specifically on Slurm..

A simplified HPC workload workflow looks like:

                    User / Researcher
                           │
                    Job Submission
                           │

                   Resource Request
                           │

                    Slurm Scheduler
                           │
    
                  Resource Allocation
                           │
              ┌────────────┴────────────┐
              │                         │ 
         CPU Compute               GPU Compute
              │                         │
              └────────────┬────────────┘
                           │
                       Application
                           │
                         Results


## Slurm

Slurm (Simple Linux Utility for Resource Management) is a workload manager and job scheduler that provides capabilities for:

- Job submission
- Resource allocation
- Job scheduling
- Queue management
- Job monitoring
- Job accounting
- Node management
- Resource enforcement

Some of the most commonly used Slurm commands include: `sinfo`, `squeue` and `sacct`


## Job Lifecycle

A workload moves through a defined lifecycle from submission to completion. A simplified lifecycle is:

                 Job Submission
                       │
                       
                    PENDING
                       │
                       │ Resources allocated
                       |
                    RUNNING
                       │
             |---------|---------|
                             
         COMPLETED   FAILED   CANCELLED


Understanding these states is important for both users and administrators.

### Job Submission

Users typically submit workloads using sbatch. For example: `sbatch job.slurm`


An example of a Slurm batch script defines the resources and commands required by the workload. 

```
#!/bin/bash

#SBATCH --job-name=cpu_example
#SBATCH --nodes=1
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=8
#SBATCH --mem=32G
#SBATCH --time=01:00:00

./application.py

```
When submitted, Slurm records the job and evaluates it against the available cluster resources and scheduling policies.

### Pending Jobs

A submitted job does not necessarily start immediately. A job may remain in the **PENDING** state while waiting for resources or other scheduling conditions.Common reasons a Job remains Pending:

```
Job Submitted
      │
   PENDING STATE
      │
      ├── Resources unavailable (e.g., waiting for nodes or GPUs)
      ├── Higher-priority jobs (queued ahead of yours)
      ├── Job dependencies (waiting for a previous job to finish)
      ├── Partition restrictions (exceeding time or node limits)
      └── Scheduling policy (such as fair-share limits)

```
#### Troubleshooting Pending Jobs

> Understanding why a job is pending is an important skill for an HPC engineers and support operations.
We can inspect a queue using the following standard commands:
- `squeue -j <job_id>` can be used to inspect the job.

- `scontrol show job <job_id>`  with this command we can obtain details information about the job. 


### Running Jobs

When Slurm determines that the required resources are available and scheduling policies allow the workload to run, resources are allocated and the job enters the RUNNING state.

The allocation may include: Compute nodes, CPU cores, System memory, GPUs, Time allocation and other configured resources.

The workload then executes within that allocation.

### Completed and Failed Jobs

A successful workload typically ends in **COMPLETED** or **FAILED**, or another terminal state such as: **CANCELLED**, **TIMEOUT**, **OUT_OF_MEMORY**.


The exact states depend on the reason the job ended and the cluster configuration, and this historical information can be inspected using: `sacct -j <job_id>`

## Requesting resources 
> Resource requests should be aligned with the actual workload. 

- Requesting substantially more resources than the application needs can result in:

      - Longer queue times
      - Lower cluster utilization
      - Resources remaining idle
      - Reduced scheduling efficiency


- Requesting too few resources can result in:

      - Poor performance
      - Out-of-memory failures
      - Insufficient CPU capacity
      - GPU underutilization
      - Job termination

> Good resource requests improve both individual workload performance and overall cluster utilization.