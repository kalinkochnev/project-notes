[Storrs HPC wiki](https://kb.uconn.edu/space/SH/26024084708/Storrs+HPC)
[AnyConnect VPN setup](https://kb.uconn.edu/space/IKB/10907091023/Cisco+AnyConnect+VPN#Red-Hat-Enterprise-Linux-8-Installation-Instructions)

# Login
- `ssh kak21001@hpc2.storrs.hpc.uconn.edu`
# Terminology
**Head node** - coordinates jobs across compute nodes

**SLURM** - program that runs on head node and coordinates jobs
- Factors that affect which jobs to run:
	- how long a job has been pending
	- number of cores for job
	- number of jobs a user has already submitted

**login node** - node you initially connect to. DO NOT RUN CODE HERE.
**compute node** - the machines a job executes on. Must be scheduled
# Flow
1. Initial ssh brings you to login node
2. Configure a bash script with the required compute resources
ex: 
```
#!/bin/bash
#SBATCH --ntasks=1    # Job only requires 1 CPU core
#SBATCH --time=5      # Job should run for no more than 5 minutes
echo "Hello, World"   # The actual command to run
```
3. Submit a job using sbatch
```
sbatch myJob.sh
```
## Interactive jobs
- Interact with real time applications like jupyter notebook, matlab, etc
- Use `srun` and `fisbatch`
```
srun --x11 -n 1 -t 1:00:00 --pty bash
```
- --x11 = this is important for some programs
- -n = asking for 1 core
- -t = asking for 1 hour
- --pty bash = gives a terminal you can type bash commands in

Additional flags
- `-n 10 -N 1` = combining these two flags means you get 10 cores on a single node
- `--mem=10G` = asking for 10 gigabytes of memory
- `--gres=gpu:1` = asking for 1 gpu

## Scheduled jobs `sbatch`

# `squeue`
View state of jobs
- View my currently running jobs

## Job state codes
```
Jobs typically pass through several states in the course of their execution.  The typical states are PENDING, RUNNING, SUSPENDED, COMPLETING, and COMPLETED.  An explanation of each state follows.

BF  BOOT_FAIL       Job terminated due to launch failure, typically due to a hardware failure (e.g. unable to boot the node or block and the job can not be requeued).

CA  CANCELLED       Job was explicitly cancelled by the user or system administrator.  The job may or may not have been initiated.

CD  COMPLETED       Job has terminated all processes on all nodes with an exit code of zero.
CF  CONFIGURING     Job has been allocated resources, but are waiting for them to become ready for use (e.g. booting).

CG  COMPLETING      Job is in the process of completing. Some processes on some nodes may still be active.

DL  DEADLINE        Job terminated on deadline.

F   FAILED          Job terminated with non-zero exit code or other failure condition.

NF  NODE_FAIL       Job terminated due to failure of one or more allocated nodes.

OOM OUT_OF_MEMORY   Job experienced out of memory error.

PD  PENDING         Job is awaiting resource allocation.

PR  PREEMPTED       Job terminated due to preemption.

R   RUNNING         Job currently has an allocation.

RD  RESV_DEL_HOLD   Job is being held after requested reservation was deleted.

RF  REQUEUE_FED     Job is being requeued by a federation.

RH  REQUEUE_HOLD    Held job is being requeued.

RQ  REQUEUED        Completing job is being requeued.

RS  RESIZING        Job is about to change size.

RV  REVOKED         Sibling was removed from cluster due to other cluster starting the job.

SI  SIGNALING       Job is being signaled.

SE  SPECIAL_EXIT    The job was requeued in a special state. This state can be set by users, typically in EpilogSlurmctld, if the job has terminated with a particular exit value.

SO  STAGE_OUT       Job is staging out files.

ST  STOPPED         Job has an allocation, but execution has been stopped with SIGSTOP signal.  CPUS have been retained by this job.

S   SUSPENDED       Job has an allocation, but execution has been suspended and CPUs have been released for other jobs.

TO  TIMEOUT         Job terminated upon reaching its time limit.
```


### Env variables
https://slurm.schedmd.com/sbatch.html

**The following variables are set by SLURM when bash script is invoked**
`SLURM_SUBMIT_DIR` - Directory from which sbatch was invoked. 
### Arguments
- 
### Submit job
```
sbatch myJob.sh
```
### View status
```
[NetID@login4 ~]$ ls *.out
slurm-279934.out

[NetID@login1 ~]$ cat slurm-279934.out 
Hello, World
```



# SLURM
