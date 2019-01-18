# HPC on Azure
HPC가 무엇인지 알아봅니다.
그리고 Azure에서 Iaas와 PaaS 형태로 HPC를 구성하는 내용을 소개합니다.
On-Premise와 유사한 형태로 IaaS 구축 케이스를 소개합니다.

## 목차

1. What's HPC?
2. HPC Workloads
3. HPC Application Models
4. Hardware and VMs in Azure
5. Azure HPC Infrastructure
6. Demo

## 교육자

Wan Sun Hong  
Senior Premier Filed Engineer  
whong@microsoft.com  



## What's HPC

High Performance Computing
그리드 컴퓨팅, 병렬 컴퓨팅으로 불리우는 포괄적인 방식의 컴퓨팅 방식



#### Windows HPC Pack 소개

- **Free add-on to Windows Server to create HPC Cluster**
  - (Compute Server 2003 -> HPC Pack 2008 R2 / 2012 R2 / 2016)
  - Latest Version: HPC Pack 2016 Update 1
  - [System Requirements](https://docs.microsoft.com/en-us/powershell/high-performance-computing/system-requirements-for-hpc-pack-2016?view=hpc16-ps)



- **HPC Pack provides you**
  - Job & Resource Scheduler
  - Distributed Runtime: Sweep, MPI, SOA, Excel UDT
  - Cluster Manager: Configuration, Nodes and Job Management, Diagnostics, Reports, ...
  - Client API, Management API, Logging API
  - Web Portal, Debugging Tools, ...



- **HPC Pack Cluster Manager**
  - Node
    - Head Node: 클러스터를 관리하는 노드 (이중화 구성 가능)
    - Compute Node: 실제로 연산 업무를 수행하는 노드
  - Network
    - Enterprise Network: Public Network
    - Private Network
  - 



