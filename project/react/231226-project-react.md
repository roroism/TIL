# TODAY I LEARNED

## Learned

### TDD(Test-Driven Development)를 활용하기

#### TDD는 어떻게 사용하나요?

1. 실패하는 테스트 작성

```javascript
test('그룹명을 입력하지 않고, 저장할 경우 에러 메시지 노출', () => {
    expect(false).toBe(true)
})
```

- 테스트 시나리오를 메소드화 한다는 것에 촛점을 맞춘다.
- 테스트 메소드명은 ‘어떤 것을 테스트하고자 하는지' 목적을 담자.
- 핵심 로직을 검증하는 단계가 아니므로, 우선 테스트는 실패하도록 한다.

2. 테스트 통과 시키기

```javascript
test('그룹명을 입력하지 않고, 저장할 경우 에러 메세지 노출', () => {
    render(<CreatingGroup/>)
    
    const saveButton = screen.getByText('저장')
    fireEvent.click(saveButton)
    
    await waitFor(() => {
        expect(getByText('그룹명을 입력해 주세요')).toBeInTheDocument()
    })
})
```

- 테스트를 통과 시킬 만큼의 코드만 구현하는 과정.
- 목(Mock) 객체 활용
    - 목(Mock) 객체 = 가짜 객체
    - 소프트웨어란 결국, 객체 간의 통신을 통해 사용자에게 기능을 제공하는 것인데,
    - 한 객체를 테스트 하기 위해서 엮인 모든 객체(혹은 외부와의 통신)를 다 initialize 하고 기능을 테스트 하기란 비효율 적임
    - 객체 간의 의존성을 다 충족 시키는 것에 집중하다 보면 실제 객체의 기능 테스트 본질도 흐려짐
    - 따라서 대상 객체에서 직접 참조하는 객체들은 mock 객체로 대체 → 발생하는 이벤트에 대해 대상 객체가 mock 객체와 어떻게 소통할 지 직접 지정할 수 있다 → 대상 객체를 테스팅 하는데에만 집중할 수 있다.

