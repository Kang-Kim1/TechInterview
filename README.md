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
      - 1.   ㅇㅇ
       
    * 단점
   
### 2. Thread
<img src = "https://user-images.githubusercontent.com/20007119/113556874-1172c000-9638-11eb-912a-f164a97ae2a0.png" width="400px">
1. 프로세스 내에서 실행되는 여러 동작의 단위 == 프로세스의 특정 수행 경로
2. 프로세스로부터 Stack 영역만 따로 할당 받고, 나머지 3개 영역(Code, Data, Heap)은 공유
 * Multi-Processing 
 * Multi-Threading

2. Java
 * Galbage Collector
 * Mutable & Immutable
 
3. DB
 * View
 * Stored Procedure
 
