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

36분

## 