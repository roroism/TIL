# TODAY I LEARNED

## Learned

### Delete 연산자

delete 연산자는 객체의 속성을 제거합니다.
제거한 객체의 참조를 어디에서도 사용하지 않는다면 나중에 자원을 회수합니다.

코드 예

```javascript
const deleteToDo = (key) => {
    const newToDos = { ...toDos };
    delete newToDos[key];
    setToDos(newToDos);
    saveToDos(newToDos);
}
```

### Alert

지정된 제목과 메시지로 경고 대화 상자를 실행합니다.

