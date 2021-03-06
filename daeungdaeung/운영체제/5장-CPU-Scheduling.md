## [CPU Scheduling 1](https://core.ewha.ac.kr/publicview/C0101020140328151311578473?vmode=f)



### Scheduling Criteria

Performance Index (= Performance Measure, 성능 척도)

- CPU utilization (이용률)

  - keep the **CPU as busy as possible**
- Throughput (처리량)

  - 	**&#35; of processes** that **complete** their execution per time unit
- Turnaround time (소요시간, 반환시간)
  - amount of time **to execute a particular process**
- Waiting time (대기 시간)
  - amount of time a process has been **waiting in the ready queue**
- Response time (응답 시간)
  - amount of time it takes **from when a request was submitted until the first response is produced.** not output(for time-sharing environment)



### Scheduling Algorithms

- FCFS (First-Come First-Served)

  - Waiting time for P1 = 0, P2 = 24, P3 = 27
  - Average waiting time: (0 + 24 + 27) / 3 = 17
  - **Convoy effect**: short process behind long process

- SFJ (Shortest-Job-First)

  - 각 프로세스의 다음번 **CPU burst time**을 가지고 스케줄링에 활용

  - CPU burst time이 가장 짧은 프로세스를 제일 먼저 스케줄

  - Two schemes

    - Nonpreemptive
      - 일단 CPU를 잡으면 이번 CPU burst가 완료될 때까지 CPU를 선점(preemptive) 당하지 않음
    - Preemtiptive
      - 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 CPU burst time을 가지는 새로운 프로세스가 도착하면 CPU를 빼앗음
      - 이 방법을 Shortest-Remaining-Time-First (SRTF) 라고 부릅니다.

  - SJF is **optimal**

    - 주어진 프로세스들에 대해 **minimum average waiting time** 을 보장합니다. (**Preemptive**)

  - 문제점

    - **평생 CPU를 선점하지 못하는 프로세스**가 생길 수 있습니다.

    - CPU Burst Time은 **추정치**를 사용합니다. (과거의 CPU burst time을 이용해서 추정)

      - exponential averaging

        - 1. $$
             t_n = \text{actual length of } n^{th} \text{CPU burst}
             $$
        
          2. $$
             \tau_{n+1} = \text{predicted value for the next CPU burst}
             $$
        
          3. $$
             \alpha, 0 \le \alpha \le 1
             $$
        
          4. $$
             \text{Define: } \tau_{n+1} = \alpha t_n + (1-\alpha) \tau_n
             $$
        
        - 수식의 오른쪽을 풀면 그 의미는 **최근에 CPU를 사용한 시간을 조금 더 중점적으로 고려**합니다.
  
- Priority Scheduling `(0:47:59)`

  - A **priority number** is associated with each process
  - highest priority를 가진 프로세스에게 CPU 할당
    - Preemptive
    - Nonpreemptive
  - SJF는 일종의 priority scheduling입니다.
    - priority = predicted next CPU burst time
  - Problem
    - **Starvation (기아 현상)**: low priority processes may never execute.
  - Solution
    - **Aging**: as time progresses increase the priority of the process.

- Round Robin (RR)
  - 각 프로세스는 동일한 크기의 할당 시간 (**time quantum**)을 가집니다. (일반적으로 10-100 ms)
  - 할당 시간이 지나면 프로세스는 선점(preemptive)당하고 ready queue의 제일 뒤에 가서 다시 줄을 섭니다.
  - n 개의 프로세스가 ready queue에 있고 할당 시간이 q time unit 이라면 **어떤 프로세스도 (n-1)q time unit 이상 CPU를 할당 받기 위해 기다리지 않습니다.**
  - Performance
    - q large => FCFS
    - q small => **context switch** 오버헤드가 커짐
    - 일반적으로 SJF보다 **average turnaround time이 길지**만 **response time은 짧습**니다.

## [CPU Scheduling 2 / Process Synchronization 1](https://core.ewha.ac.kr/publicview/C0101020140401134252676046?vmode=f)



- Multilevel Queue
  ![](imgs/5_multilevel_queue.png)
  - Ready queue를 여러 개로 분할
    - **foreground** (interactive)
    - **background** (batch - no human interaction)
  - 각 큐는 독립적인 스케줄링 알고리즘을 가집니다.
    - foreground - RR
    - background - FCFS
  - 큐에 대한 스케줄링이 필요
    - Fixed priority scheduling
      - serve all from foreground then from background
      - Possibility of **starvation**
    - Time slice
      - 각 큐에 CPU time을 적절한 비율로 할당
      - Ex) 80% to foreground in RR, 20% to backgound in FCFS
- Multilevel Feddback Queue
  - Multilevel queue를 개선
  - 프로세스가 다른 큐로 이동 가능
  - 에이징(aging)을 이와 같은 방식으로 구현할 수 있다.
  - Multilevel-feedback-queue scheduler를 정의하는 파라미터들
    - **Queue의 수**
    - 각 큐의 **scheduling algorithm**
    - Process를 상위 큐로 보내는 기준
    - Process를 하위 큐로 내쫓는 기준
    - 프로세스가 CPU 서비스를 받으려 할 때 **들어갈 큐를 결정하는 기준**
- Multiple-Processor Scheduling
  - CPU가 여러 개인 경우 스케줄링은 더욱 복잡해집니다.
  - Homogeneous processor인 경우
    - Queue에 한줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있다.
    - 반드시 특정 프로세서에서 수행되어야 하는 프로세스가 있는 경우에는 문제가 더 복잡해집니다.
  - Load sharing
    - 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘 필요
    - 별개의 큐를 두는 방법 vs. 공동 큐를 사용하는 방법
  - Symmetric Multiprocessing (SMP)
    - 각 프로세서가 각자 알아서 스케줄링 결정
  - Asymmetric Multiprocessing
    - 하나의 프로세서가 시스템 데이터의 접근과 공유를 책임지고 나머지 프로세서는 거기에 따름
- Real-Time Scheduling
  - Hard real-time systems
    - Hard real-time task 는 정해진 시간 안에 **반드시** 끝내도록 스케줄링해야 함
  - Soft real-time computing
    - **Soft real-time task**는 일반 프로세스에 비해 높은 priority를 갖도록 해야 함
- Thread Scheduling
  - Local Scheduling
    - User level thread의 경우 **사용자 수준의 thread library**에 의해 어떤 thread를 스케줄할지 결정
  - Global Scheduling
    - Kernel level thread의 경우 일반 프로세스와 마찬 가지로 **커널의 단기 스케줄러**가 어떤 thread를 스케줄할지 결정

### Algorithm Evaluation

- Queueing models
  - 확률 분포로 주어지는 **arrival rate**와 **service rate** 등을 통해 각종 **performance** index 값을 계산
- Implementation (구현) & Measurement (성능 측정)
  - 실제 시스템에 알고리즘을 구현하여 **실제 작업(workload)**에 대해서 성능을 측정 비교
- Simulation (모의 실험)
  - 알고리즘을 **모의 프로그램**으로 작성 후 **trace(data)**를 입력으로 하여 결과 비교

