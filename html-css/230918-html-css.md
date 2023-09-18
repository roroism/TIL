# TODAY I LEARNED

## Learned

### 코드는 짧고 사연은 길다

#### grid track/item 정렬

##### grid item 정렬(트랙)

```css
.container {
    display: grid;
    grid: auto / repeat(3, auto);
    place-content: end center;
}
```

- 사실 이 코드는 그렇게 실무에서 많이 사용되는 코드는 아니다.
- 트랙의 크기가 auto인 상태로 컨테이너를 가득 채우지 않는다면 트랙의 위치를 정렬할 수 있다.

##### grid item 정렬(아이템 복수)

```css
.container { 
    display: grid;
    grid: auto / repeat(3, 1fr);
    place-items: end center;
    /*<self-position> = center | start | end*/
}
```

- 실무에서 많이 쓰는 코드는 아니다.

##### grid item 정렬(아이템 단수)

```css
.container { 
    display: grid;
    grid: auto / repeat(3, 1fr);
}
.item1 {
	place-self: end center;
}
```

- 실무에서 많이 사용하지 않는다.
- 셀(복수)의 위치를 정렬할 수 있다.
- grid area 영역 안에서 아이템을 단 하나만 독립적으로 방향을 제어할 수 있다.

##### grid dense

- dense 는 밀집한다는 의미이다.
- grid를 자동으로 밀집해서 흐르게할 때 사용한다.
- 비어있는 공간을 매우는 기능이다.
- 채우지 못한 빈 영역이 있으면 흐름 방향을 거슬러 올라 트랙을 채운다.
- dense라는 속성 값은 auto-flow라는 속성 값과 항상 함께 쓰인다.

##### Grid auto-fill/fit

- auto-fill 은 힘의 방향이 안쪽으로 작용한다.
- auto-fit 은 바깥쪽으로 잡아 늘리는 방향으로 작용한다.
- 트랙을 채우지 못한 상황에서 트랙의 최대 크기가 auto이면 auto-fill 또는 auto-fit 방식으로 트랙의 크기와 수량을 자동으로 결정한다.
- 자동으로 어떻게 결정될지 정확하게 알기 어렵기 때문에 잘 사용하는 속성은 아니다.

