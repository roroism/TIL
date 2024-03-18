# TODAY I LEARNED

## Learned

### onclick vs addEventListener

- javascript에서는 요소에 클릭 이벤트를 발생시킬 때 onclick과 addEventListener 두가지 방식을 사용합니다.
- 둘 다 클릭 이벤트를 발생시키지만 각각 차이점이 존재합니다.

#### 이벤트 덮어쓰기 vs 이벤트 누적

##### onclick

- 이벤트를 여러 개 적용하는 것이 불가능. click 이벤트 핸들러가 이미 있는 상태에서 onclick으로 이벤트를 추가한다면 기존의 이벤트를 덮어씁니다.

##### addEventListener

- addEventListener를 사용하여 여러번 이벤트를 추가하면 모든 이벤트가 누적되어 동작합니다.

#### 브라우저 호환성

##### onclick

- 모든 브라우저에서 호환이 가능하다.

##### addEventListener

- IE 6,7,8 버전에서는 호환되지 않는다.

#### 버블링 캡처링

##### addEventListener

- addEventListener를 사용하면 세 번째 파라미터로 이벤트가 발생할 때 버블링으로 작동될 지 캡처링으로 작동될지 정할 수 있다.
- 세 번째 파라미터로 true를 지정하면 캡처링 타이밍에 동작하고, false를 지정하면 버블링 타이밍에 동작한다.(default는 false)

```javascript
element.addEventListener('click', 이벤트 리스너, 캡처링 버블링 선택);
```

참고
https://beforb.tistory.com/37

