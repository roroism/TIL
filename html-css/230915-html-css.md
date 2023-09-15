# TODAY I LEARNED

## Learned

### 코드는 짧고 사연은 길다

#### grid track 생성(방향)

```css
.container {
    display: grid;
    grid: 1fr 2fr / auto-flow; /* column방향으로 컬럼이 진행이 된다. */
    grid: auto-flow / 1fr 2fr; /* 행으로 배치가 된다. */
}
```

- 배치 방향 설정.
- grid track에서 설정한 방향으로 item들이 배치가 된다.
- auto-flow라는 값을 넣는 위치에 따라서 그 부분의 방향이 결정이 된다.
- auto-flow 값은 grid 단축 속성에서만 사용하는 값의 형태로 grid-auto-flow 속성값의 다른 표기법.
- 슬래시(/)와 함께 교차 축 grid-template-rows/columns 값의 명시가 필수.

#### grid item의 배치와 병합

#### grid item 배치

```css
.container {
    display: grid;
    grid: auto / repeat(3, 1fr);
}
.item1 { grid-area: 2 / 3; }
```

- 행 배치 시점 / 열 배치 시점 / 행 배치 종점 / 열 배치 종점 값을 선언하여 아이템의 배치 위치를 결정할 수 있다.
- 값은 시계 반대 방향으로 순환하고 슬래시(/) 구분자로 분리한다.
- 생략한 값은 auto와 같다.

#### grid item (배치/병합 실무에서 사용할 확률 높음)

```css
.container {
    display: grid;
    grid: auto / repeat(3, 1fr);
}
.item1 { grid-area: 2 / 2 / span 3 / span 2; }
```

- span 키워드와 병합할 트랙의 수량을 조합하면 셀을 병합할 수 있다.
- 우리가 grid를 사용하기로 마음먹었다면 분명히 컬럼을 병합할 만한 상황이 있기 때문일 것이다.
- flex에서는 이런한 것을 구현할 수 없기 때문에 이 문법을 알아두는 것이 중요하다.

