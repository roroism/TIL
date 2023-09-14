# TODAY I LEARNED

## Learned

### 코드는 짧고 사연은 길다

#### drid track 생성(반복)

```css
.container {
    display: grid;
    grid: auto / 40px 1fr 2fr 1fr 2fr;
    grid: auto / 40px repeat(2, 1fr 2fr);
}
```

- auto 값으로 트랙의 크기 임의 지정 가능.
- `repeat()` 함수로 크기 값을 반복할 수 있다.
- 함수의 첫 번째 인자는 트랙의 수량, 두 번째 인자는 트랙의 크기.
- `repeat(<integer [1, 무한]>`, <track-list>) // 반복할 횟수, 반복 패턴
- 트랙의 크기가 한정된 경우에 repeat 함수를 사용할 수 있다.

