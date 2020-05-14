## 1. Hello World! 프로그램 

<img width="960" alt="1" src="https://user-images.githubusercontent.com/62346198/81900362-96f01a80-95f7-11ea-9822-6bed5f39f9aa.PNG">

- OllyDbg 창 
  1. Code Window : 기본적으로 disassembly code 를 표히사여 각종 comment, label을 보여주며, 코드를 분석하여 loop, jump 위치 등의 정보를 표시합니다.
  2. Register window : CPU register 값을 실시간으로 표시하며 특성 register 들은 수정도 가능합니다.
  3. Dump window : 프로세스에서 원하는 memory 주소 위치를 Hex 와 ASCII/유니코드 값으로 표시하고 수정도 가능합니다.
  4. Stack window : ESP register가 가리키는 프로세스 stack memory를 실시간으로 표시하고 수정도 가능합니다. 
  
- 기본 명령어
  - Restart [Ctrl+F2] : 다시 처음부터 디버깅 시작 (디버깅을 당하는 프로세스를 종료하고 재실행)
  - Step Into [F7] : 하나의 OP code실행 (CALL 명령을 만나면, 그 함수 코드 내부로 따라 들어감)
  - Step over [F8] : 하나의 OP code실행 (CALL 명령을 만나면, 따라 들어가지 않고 그냥 함수 자체를 실행)
  - Execute till Return [Ctrl+F9] : 함수 코드 내에서 RETN명령어 실행 (함수 탈출 목적)
- 디버거 동작 명령
  - Go to [Ctrl+G] : 원하는 주소로 이동 (코드/메모리를 확인할 때 사용. 실행되는것은 아님)
  - Execute till Cursor [F4] : cursor위치까지 실행 (디버깅하고 싶은 주소까지 바로 갈 수 있음)
  - Comment [;] : Comment 추가
  - User-defined comment : 마우스 우측 메뉴 Search for User-defined comment
  - Label : Label 추가
  - User-defined label : 마우스 우측 메뉴 Search for User-defined label
  - Set/Reset BreakPoint [F2] : BP설정/해제
  - Run [F9] : 실행 (BP가 걸려있으면 그곳에서 실행이 정지됨)
  - Show the current EIP [\*] : 현재 EIP위치를 보여줌
  - Show the previous Cursor [-] : 직전 커서 위치를 다시 보여줌
  - Preview CALL/JMP address [Enter] : 커서가 CALL/JMP등의 명령어에 위치해 있다면, 해당 주소를 따라가서 보여줌
  
- 베이스캠프를 설치하는 방법
  - Goto 명령 [Ctrl+G}
  - BP 설치 [F2]
  - 주석 [;]
  - 레이블 [:]
  
- All referenced txet string : 프로그램에서 참조되는 문자엳릉를 보여주는 창이 뜸
- All intermodular calls : 코드에서 사용된 API 호출 목록 창 뜸
    - API ~ 윈도우 프로그래밍에서 모니터 화면에 뭔가를 출력하려면 Win32 API를 사용하여 OS에게 화면출력을 요청함 
    - But Packer/Protector를 사용하여 실행파일을 압축/보호 했다면 OllyDbg에서 API호출 목록이 보이지 X
 ## 2. 문자열 패치
1. 문자열 버퍼를 직접 수정 : [Ctrl+E] Edit 다이얼로그 
  원본보다 더 큰 문자열을 덮어쓸 때는 그 뒤 데이터를 훼손하지 않도록 매우 조심
2. 다른 메모리 영역에 새로운 문자열을 생성하여 전달

## 3. Assembly 기초 명령어
- CALL XXXX : XXXX주소의 함수를 호출
- JMP XXXX : XXXX주소로 점프
- PUSH XXXX : 스택에 XXXX 저장
- RETN : 스택에 저장된 복귀 주소로 점프 
