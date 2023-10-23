# TODAY I LEARNED

## Learned

### Flex

#### flex

- 초기값 : 0 1 auto
- flex-grow: 0 flex-shrink: 1 flex-basis: auto

##### flex-grow

- 형제 아이템들이 모두 동일한 flex-grow 값 = 동일한 공간
- 형제 아이템들이 다른 flex-grow 값 = 다른 공간

##### flex-shrink

- item들이 flex container를 넘어가지 않으면 줄어들 필요가 없을 것이다. flex-shrink는 item들이 flex container 를 넘어갈 때, 그 때 어떻게 줄어들 것이냐를 설정한다.
- flex-shrink: 0 = 줄어들지 않겠다!

##### flex-basis

- 아이템의 초기 크기
- ‘auto가 아닌 flex-basis’와 ‘width(direction: column이면 height)’ 중 flex-basis가 우선.

