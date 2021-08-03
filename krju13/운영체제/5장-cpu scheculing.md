## [CPU Scheduling](https://core.ewha.ac.kr/publicview/C0101020140328151311578473?vmode=f)

nonpreemptive 비선점형(강제로 뺏지 않는 방법)  
preemptive 선점형(강제로 뺏는 방법)

## 성능척도 scheduling criteria
시스템 입장
- cpu utilization 이용률  
  전체 시간 중에서 cpu가 놀지 않는 시간(가능하면 바쁘게 만들기)
- Throughput 처리량  
   주어진 시간 동안 몇개 일을 처리했느냐?
  
소프트웨어 입장 ( 프로세스 끝날 때까지를 생각하는게 아니고 cpu 쓰러 들어와서 io하러 나가기 전까지의 시간)
- Turnaround time 소요시간, 반환시간  
  cpu 쓰러 들어와서 다쓰고 나가는 데 걸리는 시간. cpu burst 하고 나간 시간
- waiting time 대기시간  
  기다린 시간 
- response time 응답 시간  
  처음 cpu를 사용하게 된 시간 
  


## FCFS(First-come first-served)
먼저온 사람 먼저   
(비선점형)  
효율적이지 않다.  
앞에 어떤 프로세스를 하냐에 따라 다르다.  
이렇게 오래 기다리는 것은 convoy effect: 앞에 똥차가 있는 경우  

## sjf(shortest-job-first)
cpu-burst 가 짧은 프로세스부터 스케줄
2가지 방법  
-비선점  
    - 일단 cpu 잡으면 이 cpu burst가 완료될때까지 수행  
-선점  
    - 수행중인 애보다 더 짧은 cpu burst가 오면 뺐어서 하는건데   
      Shortest-remaining-time-first(srtf)이라고 부른다.  

문제점  
1. 기아현상(stavatopm)  


2. cpu 사용 시간을 미리 알 수가 없다.  
    추정은 가능 하다.




## 다음 CPU Burst Time의 예측
다음번 CPU burst time을 어떻게 알 수 있을 까?  
추정이 가능하다.  
과거의 CPU burst time 을 이용해서 추정한다.  
1. tn= actual lenght of n-th CPU burst
2. Tn+1= predicted value for the next CPU burst
3. a(알파) 0 <= a <= 1
4. Define: Tn+1= atn+(1-a)Tn
n+1 번째 예측시간은 n번째 실제 걸린 시간 * a + (1-a)* n번째 예측 시간 
   
점화식을 풀면
Tn+1 = atn +(1-a)atn-1  + ... 
      + (1-a)^j a tn-j  + ...
      + (1-a)^n+1 t0


## priority Scheduling 우선순위 스케줄링
우선순위가 높은 프로세스 먼저
- 선점
  더 높은 우선순위인 프로세스가 오면 뺏는거
- 비선점
    뺏지는 않는다. 
  
우선순위가 높으면 정수중에 제일 작은 수로 준다. 

- SJF역시 일종의 우선순위 스케줄링이 된다.

문제점은 우선순위가 낮은 아이가 기아현상이 생긴다는 것

솔루션: 
aging= 노화 (나이를 먹으면 솔루션의 우선순위를 올려주는 것)


## Round Robin (RR)
- 각 프로세스는 동일한 크기의 할당시간을 가짐 ( 일반적으로 10~100 밀리 세컨드 임)
- 할당 시간이 지나면 프로세스는 레디큐의 제일 뒤에 가서 다시 줄을 선다.
- n개의 프로세스가 레디큐에 있고 할당 시간이 q인 경우
각 프로세스는 최대 q 단위로 cpu 시간의 1/n을 얻는다. 
  => 어떤 프로세스도 (n-1)q time unit 이상 기다리지 않는다.
  
- performance
-   q large => FCFS
- 1 small => context switch 오버헤드가 커진다. 

