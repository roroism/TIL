# TODAY I LEARNED

## Learned

### 시스템 설계 (2) - Sequence diagram

#### 어떻게 사용하나요?

##### 구성 요소

- 생명선 (Lifeline) : 객체가 메모리 상에 얼마나 오래 살아있는지 나타내는 선. 아래로 내려갈 수록 시간이 경과됨을 의미.
- 객체/참여자 (Participant).
    - 사용자
    - 데이터베이스
    - 시스템
    - 클래스
- 메시지 (Message) : 객체간 그리고 참여자 간에 어떤 메세지를 주고 받는지를 기술하는 것. 메세지는 기본적으로 화살표로 나타낸다.
    - 동기 (Synchronous) : 동기 요청
    - 비동기 (Asynchronous) : 비동기 요청
    - 자체 (Self) : 표기하지 않아도 되지만, 중요한 것은 표기할 수도 있다.
    - 반환 (Return) : 응답에 대한 메세지
        동기 반환 (Sync. return)
	비동기 반환 (Async. return)
- 활성 상자 (Activation box) : Lifeline 위에 그려지는 네모 박스로, 이 시간 동안은 해당 객체가 활성화 되어 있는 것을 의미.
- Guard : 단일 메세지에 대해 조건을 명시하는 방법.
- Sequence Fragments : 특정 sequence 범위에 대해 조건을 명시하는 방법.
    - Alt. = If/else 문을 의미한다.
    - Loop = while 문을 의미한다.
    - Options = If 문을 의미한다.

