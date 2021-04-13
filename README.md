# Technical Interview
### 1. Process
<img src = "https://user-images.githubusercontent.com/20007119/113556392-5cd89e80-9637-11eb-8142-f57a5c29d7b4.png" width="400px">

1. 실행되고 있는 프로그램의 인스턴스 (== OS로부터 시스템 자원을 할당받은 단위)
2. Code, Data, Stack, Heap 를 포함하고 있는 독립된 영역
    * Code : 프로그램의 코드가 저장되는 영역 (컴파일 시 크기 결정)  
    * Data : Static, Global 변수, 정적 배열 등 컴파일 시 크기가 결정되는 data 영역 (컴파일 시 크기 결정)  
    * Stack : 지역변수, 함수 리턴값 등 임시 데이터가 영역 (런타임 시 크기 결정)  
    * Heap : new 키워드를 통한 객체 생성 등 동적 할당되는 객체 영역 (런타임 시 크기 결정)  
3. 각 프로세스는 별도의 주소공간에서 실행되며, 다른 프로세스 접근 시 파이프라인, 소켓 등 활용
4. 기본적으로 최소 1개 스레드(main thread) 포함 
5. Multi-Processing
    * 장점
      1. 문제 발생 시, 자식 프로세스 제거 > 추가적인 악영향 최소화
    * 단점
      1. Context Switching(프로세스간 교대 시, 마지막 상태를 복구하는 작업)에 많은 리소스 소요
      2. 독립된 메모리 영역을 사용하고 있어, 프로세스간 데이터 공유 어려움
      3. 
   
### 2. Thread
<img src = "https://user-images.githubusercontent.com/20007119/113556874-1172c000-9638-11eb-912a-f164a97ae2a0.png" width="400px">
1. 프로세스 내에서 실행되는 여러 동작의 단위 == 프로세스의 특정 수행 경로
2. 프로세스로부터 Stack 영역만 따로 할당 받고, 나머지 3개 영역(Code, Data, Heap)은 공유
3. Multi-Threading

### 3. Galbage Collector
1. JVM에서 불필요한 메모리를 정리
2. GC 실행 시, 모든 스레드는 정지되며 GC 스레드만 동작하게 됨(Stop-The-World)
3. Heap 영역은 '대부분의 객체가 일회성'이며 '오래 지속되는 경우가 드물다'는 전제로 아래와 같이 영역을 분리
    * Young Generation 
      - 새롭게 생긴 객체가 할당되는 영역
      - Eden, 2개의 Survier 영역으로 나뉨
        * new로 객체 할당 > Eden 영역에 위치 > GC발생 > 살아남은 객체 Survivor로 이동 
      - 해당 영역 GC : Minor GC 
      - 대부분의 객체가 해당 영역에서 접근 불가한 상태로 변경
    * Old Generation
      - Young 영역에서 Reachable 상태를 유지한 객체가 복사 이동되는 영역 == Y.G. Survivor 영역 가득 찬 시점에 남은 객체
      - Young 대비 큰 영역 할당, GC 덜 발생
      - 기본적으로 Data가 가득 찼을떄  GC 수행
      - Card Table : 해당 영역에서 Young 영역 객체를 참조하는 객체 정보를 저장함 (512Byte Chunk)
      - 해당 영역 GC : Major GC & Full GC
      
3. GC 방식
    1. Serial GC
       * Old영역으로 넘어간 객체를 mark-sweep-compact 알고리즘을 사용하여 아래와 같이 Garbage 식별
       * 진행 순서 : 
         1. 살아있는 객체 식별(mark)
         2. 살아있는 객체 남김를 제외한 Garbage 삭제(sweep) 
         3. 남은 객체는 Heap의 앞부분부터 정렬되도록 정리(compact)
    2. Parallel GC (Throughput GC)
       * Serial GC와 동일하나 다중 스레드로 수행. 메모리가 충분하고, 코어 개수가 많을수록 유리
    3. Parallel Old GC
       * Young 영역은 Parallel과 동일하지만 Old 영역에서 Sweep 과정 대신 살아있는 객체를 식별
    7. CMS(Concurrent Mark Sweep) GC 
       * Stop-The-World 시간을 크게 줄일 수 있으나, 메모리와 CPU를 많이 사용함
       * Compaction 단계가 없음 (Stop-The-World 짧음)
       * 진행 순서 : 
         1. I nitial Mark : 클래스로더와 가장 가까운 객체 중 살아있는 객체 확인(Stop-The-World 발생) 
         2. Concurrent Mark : I.M에서 확인된 객체들이 참조하고 있는 객체를 찾아가며 살아있는 객체 확인
         3. Remark : C.M 단계를 진행하는 도중 새로 참조되거나 끊긴 객채를 재확인(Stop-The-World 발생)
         4. Concurrent Sweep : 참조되지 않은 객체 삭제
    8. G1(Garbage First) GC
       * Haeap를 블록단위(region)로 나눔 :
         <img src="https://user-images.githubusercontent.com/20007119/114541572-de60aa00-9c91-11eb-966c-358d9850a2e5.png" width="400px">
       * Young, 
    10. 

### 4. Mutable & Immutable
1. Immutable : 클레스의 인스턴스가 생성된 후, 내용이 바뀌지 않는 특징을 갖는 클래스 
    * int, double 등의 primitive 타입, String 등
    * 실제 값에 대한 불변이 아닌 값에 할당되는 주소값에 대한 불변 여부
2. Mutable : String을 제외한 참조타입(배열 등)

### 5. 자바 참조타입
1. 기본 타입
2. 참조 타입
3. 


### 3. DB
1. View
2. Stored Procedure
 
