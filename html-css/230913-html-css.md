# TODAY I LEARNED

## Learned

### 코드는 짧고 사연은 길다

#### grid container 생성

- display: grid | inline-grid
- 그리드 컨테이너/아이템에 선언하지 않은 모든 `grid-*` 속성은 초기값으로 설정된다.
- grid 속성으로 컨테이너의 트랙(행/열) 수와 크기를 설정하고 grid-area 속성으로 아이템의 배치와 병합을 설정하기 전까지는 그리드 컨테이너를 생성한 것 만으로 특별한 효용이 없다.

#### grid track 생성 (균등)

- grid: <'grid-template-rows'> / <'grid-template-columns'>
- display: grid를 생성한 것만으로는 아무 효과도 없기 때문에 grid 속성을 이용하여 컬럼을 생성.
- 3열의 익명 트랙 단축 문법.
- 셀 크기는 내용에 따라 자동.

```css
.container {
    display: grid;
    grid: '. . .'; /* 익명의 컬럼 3개가 생성 */
}
```

- 컬럼 트랙을 정확하게 설정하지 않는 방법이기 때문에 실무에서 자주 사용하지 않는다.

#### grid track 생성(제어) 실무 사용 확률 99%

```css
.container {
    display: grid;
    grid: 80px 1fr / 120px 1fr; /* <'grid-template-rows'> / <'grid-template-columns'> */
}
```

- 2열 2행 트랙 단축 문법.
- 트랙의 크기와 수량을 명시적으로 제어.
- 실무에서 가장 빈번하게 사용하는 패턴.
- 명시적으로 선언하지 않는 나머지 트랙은 자동.
- fr은 fraction(분수, 분할)의 약자.
- 첫번째 행의 높이가 80px가 적용되고, 나머지행은 1fr 즉, 자동으로 결정되는 높이값. / 첫번째 열의 폭은 120px으로 결정이 되고, 나머지는 1fr로 결정이 된다.

