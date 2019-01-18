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



### Mission

- 리서치 조사자, 엔지니어, 금융 분석가(Quants), 디자이너, 개발자, 데이터 사이언티스트 등에게 활용 가능하다.
- 활용 사례
  - 풍력 발전소의 바람 역학 실험
  - 자동차 충돌 실험, 자동차 바람 영향 역학 실험 (Engineering model and simulation Car crash simulation)
  - 비디오 랜더링 (Video Rendering)
  - 유전학 / 의약 (Genomics / Pharma)
  - Oil & Gas, Seismic, Reservoir Simulation
  - 금융 위기 분석 (Financial Risk Analysis)
  - Earth Science, Climate Hydrology
- 활용 가능 분야
  - Gov'T and Defense
  - Higher Education
  - Earth Sciences
  - Energy & Utilites
  - Manufacturing
  - Healthcare and Life Sciences
  - Financial Services
  - Syber Security
  - Communications and Media
  - Condsumer-Driven Industries
  - 아직도 여러 분야로 확대 중



#### Transformation Requires

- Total autonomy will only be 100% accident-free by testing a minimum of 8.8 million miles.
- Autonomous vehicles will generate and consume reougly 4,000 gigabytes of data a day by 2020.
- 20.4 billion things will be connected by 2020.
- An animated film might render as much as 65 million hours of footage to come up with 90 minutes of worhwhile materials.
- NANA's Earth Obserbving System Data and Information System (EODSIS) distributes almost 28 terabytes of data a day.
- An aireplane will generate 40 terabytes of data a day by 2020.



### 두 종류의 어플리케이션 (Two Kinds of Application)

#### Embarrassingly Parallel (처치 곤란 병렬)

- 업무를 여러 노드에 할당하여, 연산 처리하여 결과를 내놓는다.
- 작업 결과 사이의 소통이나 연관성이 필요 없는 경우
- Compute nodes don't need to talk to each other, or very little cross-node coomunication
- Usually a parameter sweep, a job splitting, or a search/comparison through data.
- Examples: Monte Carlo Simulations, Image/Video Randering, Genetic Algorithms, Sequence Matching, File Processing

#### Tighly Coupled

- 업무를 한 노드에 할당을 하고, 결과를 서로 공유한다. (노드 간의 연결성 있는 워크로드)
- Compute nodes ndeed to talk to each other constantly
- Requires a fast interconnection network (Low latency and high throughput)
- Examples: Automotive crash simulation, Fluid Dynamics, Climate Modeling, Resevoir Simulation, Manugacturing Desing



### Job Types

#### Parametric Sweep

- Referred to as "처치 곤란 병렬"



#### MPI

- Message Passing Interface is an industry standard for messaging between compute nodes
- Excutables that run on multiple cores or nodes that have dependencies
- Need to communicate with each other
  - Two Parts
    - APIs used in the program
    - Application launcher (mpiexec.exe) that controls the supplication's execution
  - C/C++, Microsoft .Net
  - Visual Studio



##### SOA Application

- Service-Oriented Architecture (SOA) is an architectural style desinged for building distributed systems



#### Microsoft Excel Offloading

- Escutes of compute-intensive Microsoft Excel weorkbooks with independent



## Hardware and VMs

### Azure

#### Infrasture Services

- Cloud Services
- Virutal Machines
- VM Scale Sets
- Containers



### Platform Services

- Compute - Batch



### Azure Hardware and VM Sizes

- A-Series
  - Entry Level VMs
  - Dev/Test Workload
- D-Series
  - General Purpose VMs
  - Common Applications, Web Servers etc
- F-Series
  - Compute Optimized VMs
  - Gaming, Analytics
- G-Series
  - Large Memory VMs
  - Large Databases
- L-Series
  - Stroage Optimized VMs
  - NoSQL Databases(Cassandra, MongoDB), Data warehousing
- H-Series (Infiniband 사용 가능)
  - High Performance VMs
  - Batch Processing, Fluid Dynamics, Monte Carlo Simulation
- N-Series (Infiniband 사용 가능)
  - GPU-enabled VMs
  - Graphic based applications,



### Virtualized RDMA

#### RDMA

- A technology for transferring data between memories over a high-speed network.
- Provides the ability to transfer remote data directly from / to memory without using a CPU. Reduces host CPU burden & contention for host memory and I/O buses.



#### Network Direct

- High Performance networking abstraction layer for IHVs
- Microsoft defined interfaces for RDMA
- Transparent support of InfitiBand, iWARP and RoCE







### Parallel File System - Lustre

- Intel Lustre is an open-source parallel file system and is used in some of the largest HPC clusters in the world due to its hight performance and scalability.
- Lustre utilizes the following concepts and components to present a unified Lustre file system.
- [Availability of STAR-CCM+ on Microsoft Azure](https://azure.microsoft.com/en-us/blog/availability-of-star-ccm-on-microsoft-azure/)









## Demo

- Create an IaaS HPC Cluster
  - IaaS VMs: Head / Broker Node, Compute Nodes
- Create a Cloud Service for worker roles
  - Create Azure node template
  - Add Azure nodes to IaaS HPC Cluster