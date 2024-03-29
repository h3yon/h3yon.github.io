# 멀티 프로세스 & IPC & 세마포어,뮤텍스



## 멀티 프로세스 & IPC & 세마포어,뮤텍스

출처: [multi process vs multi thread](https://github.com/zhsks528/neulsang/blob/c952892547bc2db5fb7f0cadb3b49096a8d62948/content/blog/multi%20process%20vs%20multi%20thread/index.md)

## 컨텍스트 스위칭

한 task가 끝날 때까지 기다리는 게 아니라 여러 작업을 번갈아가며 동시에 처리한다. 인터럽트 발생 시 프로세스 상태를 PCB에 저장하고 새로운 프로세스 상태를 레지스터에 저장한다. 이때 CPU는 아무런 일을 하지 않기 때문에 잦은 컨텍스트 스위칭은 성능저하를 야기한다.

## 멀티 프로세스

- 장점
  - 자식 프로세스 중 하나에 문제 발생 시 영향이 확산되지 않는다.
- 단점
  - IPC(Inter Process Communication)
    - 각각의 독립된 메모리 영역을 할당받았기 때문에 하나의 프로그램에 속하는 프로세스 사이의 변수를 공유할 수 없다
  - Context Switching에서의 오버헤드
    - 컨텍스트 스위칭 과정에서 캐쉬 메모리 초기화 등 무거운 작업이 진행되고 많은 시간이 소모되는 오버헤드가 발생하게 된다.
    - 프로세스는 각각의 독립된 메모리 영역을 할당 받았기 때문에 프로세스 사이에서 공유하는 메모리가 없어, 컨텍스트 스위칭이 발생하면 캐시에 있는 모든 데이터를 리셋하고 다시 캐시 정보를 불러와야 한다.

## IPC

프로세스 간의 통신 방법을 제공한다.

- IPC 기법

  - Message Queue
  - Shared Memory
  - Pipe
  - Signal
  - Semaphore
  - Socket

1. Pipe

   - 단방향 통신
   - fork()로 자식 프로세스 만들었을 때 부모와 자식 간의 통신
   - pipe는 커널 영역에 존재

2. 메시지 큐

   - FIFO이며, 양방향. 어떤 프로세스 간이든 데이터 송수신 가능

3. 공유 메모리

   - 커널 공간에 메모리 공간을 만들고 해당 공간을 변수처럼 사용
   - 메모리 주소를 변수처럼 접근
   - 공유메모리 key로 여러 프로세스가 접근 가능

4. Signal

   - 커널 또는 프로세스에서 다른 프로세스에 어떤 이벤트가 발생되었는지를 알려주는 기법
   - 미리 정의된 이벤트
   - 프로세스 관련 코드에 관련 시그널 핸들로를 등록해서 해당 시그널 처리 실행

5. 소켓

   - 두 개의 다른 컴퓨터 간의 네트워크 기반 통신 위한 기술
   - 2개의 프로세스 간 통신 기법으로 사용 가능

6. 정리
   - 대부분의 IPC 기법은 커널 공간 활용
     - 이유: 커널 공간은 프로세스 간의 공유가 가능

## 세마포어

스레드 간 전역 변수를 공유하다 보면 동기화 이슈가 발생하는데,
동기화 이슈 해결 방안에는

> 상호배제
> 동시 접근 막기
> 공유 변수에 대해서는 Exclusive Access 필요

## 뮤텍스와 세마포어

- 임계 영역에 대한 접근을 막기 위해 LOCKING 메커니즘이 필요하다.
  - 뮤텍스: 임계영역에 하나의 스레드만 들어갈 수 있다.
  - 세마포어
    - 임계 영역에 여러 스레드가 들어갈 수 있다.
    - counter를 두어 동시에 리소스에 접근할 수 있는 허용 가능한 스레드 수 제어

## 페이지 폴트

- 어떤 페이지가 실제 물리 메모리에 없을 때 일어나는 인터럽트
- 운영체제가 페이지 폴트가 일어나면, 해당 페이지를 물리 메모리에 올린다.

감사합니다!
