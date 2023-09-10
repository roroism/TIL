# TODAY I LEARNED

## Learned

### IE를 지원하지 않아도 된다면 가장 쓸모 있는 flex

#### flex container

- display: flex | inline-flex
- display : flex // 블록박스인 것처럼 랜더링이 된다.
- display : inline-flex // 인라인 블록박스인 것처럼 나란히 배치된다.

#### 플렉스 아이템의 팽창과 수축

- flex-grow
- flex-shrink
- flex-basis
- flex (추천)
- 초기값

```css
flex-grow : 0;
flex-shrink : 1;
flex-basis : auto;
flex : 0 1 auto;
```

- 실무에서는 flex-basis를 보통 0으로 설정한다.

##### flex-grow

- 양의 FS 발생 시 플렉스 아이템의 팽창을 제어.
- 음수 사용 불가. 보통 0 or 1 사용.
- 초기값 : 0, 하지만 단축 속성에서 생략하면 1이 됨.
- 적용 : flex item

##### flex-shrink

- 음의 FS 발생 시 플렉스 아이템의 수축을 제어. 음의 FS 발생 : container보다 item들의 면적들이 더 클 경우(넘칠경우)
- 음수 사용 불가. 보통 0 or 1 사용.
- 초기 값 1 // 단축 속성에서 생략해도 1이 됨. (1을 추천. flex container보다 자식 요소의 박스가 더 늘어나서 container 밖으로 나가는 상황은 보통은 선호하는 layout은 아니기 때문이다.)
- 적용 : 플렉스 아이템

##### flex-basis

- 플렉스 아이템의 진행 방향 기본 크기를 설정함으로써 FS 초기 값에 영향을 준다.
- 값 : content | // 명세에는 content를 지원한다고 하지만 아직 구현한 브라우저가 없기 때문에 실제로는 사용할 수 없다.
- 초기값 : auto // auto로 하면 content or <width> 값이 적용됨. // 보통 0으로 초기화해서 사용하길 추천하다. // 단축 속성에서 생략하면 초기 값이 0이 된다.
- 적용 : 플렉스 아이템

##### flex

- 플렉스 아이템의 '팽창, 수축, 기본 크기'를 제어하는 단축 속성.
- 값: none | [<'flex-grow'> <'flex-shrink'>? || <'flex-basis'>] // | 반드시 하나, ? 생략하거나 한 번, || 하나 또는 그 이상.
- 초기 값 : 0 1 auto // 생략한 속성의 값은 재설정(변경) 된다. // grow나 shrink는 설정하지만 flex-basis까지는 설정하지 않는다. 왜냐하면 생략하면 자동으로 0으로 세팅되기 때문이다.
- 적용 : 플렉스 아이템

#### 실무에서 많이 사용하게 될 코드

```css
.item { flex: 1 } /* 제일 많이 사용하게 될 코드 */
/* == */
.item { flex: 1 1 }
/* == */
.item { flex: 1 1 0}
/* flex-grow 또는 flex-shrink 값을 선언하면 flex-basis 값은 'auto'에서 '0'으로 변경된다. */
```

