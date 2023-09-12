# TODAY I LEARNED

## Learned

### 코드는 짧고 사연은 길다

- 격자를 이용하여 내용의 크기와 위치를 제어하는 방법.
- 특히 셀 병합 기능을 제공.
- 다른 수단에 비해 짧은 코드로 자유도 높은 배치를 구현.

#### 실무에서 사용하는 속성

- 다양한 속성들이 있지만 실제로 실무에서 자주 사용하는 속성은 컨테이너에 적용하는 grid와 item에 적용하는 grid-area 라는 속성이 있다.
- 단축속성으로 사용하는 것이 간결하고, 보기도 좋다.
- grid : 트랙의 수와 크기, 컨테이너에 적용.
- grid-area : 아이템의 배치와 병합, 아이템에 적용.

#### Grid 용어

- grid container (그리드 컨테이너)
- grid item (그리드 아이템)
- grid line (그리드 라인)
- grid track (그리드 트랙)
- grid cell (그리드 셀), grid area (그리드 영역)
- gap (갭)

#### 명시적 그리드와 암시적 그리드

- 명시적 그리드 : 트랙의 크기와 수량을 분명하게 선언. grid-template-rows/columns/areas
- 암시적 그리드 : 명시적 그리드 외부에 배치되어 흐름 방향과 크기를 결정. grid-auto-flow/rows/columns
- gap : 다중 컬럼, 플렉스, 그리드 아이템 사이의 간격.

#### grid container 역할

- 트랙의 수량과 크기를 명시. `(grid-template-*)`
- 아이템 배치 방향. `(grid-auto-flow)`
- 암시적 트랙 크기. `(grid-auto-*)`

#### grid item 역할

- 아이템의 배치와 병합, 배치 순서. (grid-row-start/-column-start/-row-end/-column-end, grid-area)

