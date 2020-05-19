## 1. CPU 레지스터란?
레지스터 : CPU 내부에 존재하는 다목적 저장 공간
~ 어셈블리 명령어의 대부분은 레지스터를 조작하고 그 내용을 검사하는 것들이라 먼저 레지스터를 알아야 함

## 2. Basic program execution registers
1. 범용 레지스터 (General Purpose Register) 32비트 : 범용적으로 막 쓰는 레지스터 / 보통은 상수/주소 등을 저장할 때 사용
  - EAX : Accumulator for operands and results data (일반적으로 함수 리턴값에 사용)
  - EBX : Pointer to data in the DS segment
  - ECX : Counter for string and loop operations (반복문 명령어에서 반복카운트로 사용)
  - EDX : I/O pointer
  주로 산술연산 명령어에서 상수/변수 값의 저장 용도로 많이 사용
  - EBP : Pointer to data on the stack (in ther SS segment) (호출되었을 때 그 순간의 ESP를 저장하고 있다가, 함수가 리턴하기 직전에 다시 ESP에 값을 되돌려줘서 스택이 깨지지 않도록 함 =>Stack frame 기법
  - ESI : source pointer for string operations
  - EDI : destination pointer for string operations
  - ESP : Stack pointer (in the SS segment) 
  주로 메모리 주소를 저장하는 포인터로 사용
2. 세그먼트 레지스터 (Segment Register) 16비트 
  세그먼트 : 메모리를 조각내어 각 조각마다 시작주소, 범위, 접근권한 등을 부여하여 메모리를 보호하는 기법
  - CS : Code Segment
  - SS : Stack Segment
  - DS : Data Segment
  - ES : Extra(Data) Segment
  - FS : Data Segment
  - GS : Data Segment
3. 플래그 레지스터 EFLAGS (Flag Register) 32비트
  각각 1비트 or 0비트의 값을 가짐, On/Off 의미함
  - ZF : Zero Flag (연산명령 후 결과값이 0이되면 ZF가 1로 세팅)
  - OF : Oveflow Flag (부호있는 수의 오버플로가 발생했을 때 1로 세팅, MSB가 변경되었을 때 1로 세팅)
  - CF : Carry Flag (부호없는 수의 오버플로가 발생했을 때 1로 세팅)
4. Instruction Pointer
  - EIP : Instruction pointer (CPU가 처리할 명령어의 주소를 나타내는 레지스터, 크기는 32비트)
  CPU는 EIP에 저장된 메모리 주소의 명령어를 하나 처리하고 난 후 자동으로 그 명령어 길이만큼 EIP증가시킴
  값은 직접 변경할 수 없고, 다른 명령어를 통해서 간접적으로 변경해야함
  
---

디버깅의 기초는 어셈블리 명령어의 이해인데, 그 명령어의 많은 부분은 레지스터를 조작하는 내용이라 레지스터를 잘 알면 디버깅을 하는데 크게 도움이 됨. 
