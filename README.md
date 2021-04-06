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
2. Heap 영역은 '대부분의 객체가 일회성'이며 '오래 지속되는 경우가 드물다'는 전제로 아래와 같이 영역을 분리
    * Young Generation
      - 새롭게 생긴 객체가 할당되는 영역
      - 대부분의 객체가 해당 영역에서 접근 불가한 상태로 변경
      - 해당 영역의 대한 GC : Minor GC 
    * Old Generation
      - Young 영역에서 Reachable 상태를 유지한 객체가 복사 이동되는 영역
      - 복사되는 과정에서 Y.G 대비 큰 영역이 할당됨


1. Mutable & Immutable
3. DB
 * View
 * Stored Procedure
 
