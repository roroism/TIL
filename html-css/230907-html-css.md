# TODAY I LEARNED

## Learned

### 레이아웃, 애증의 플로팅

#### 플로팅 속성의 의도 이해하기

- 이미지박스에 글자를 붙여서 흐르듯이 배치하기 위해 제공하는 속성.
- 하지만 컬럼 배치를 위해 사용하는 경우가 대부분.
- 플로팅이 이해하기 어려운 이유는 글자는 흐르듯이 배치되는데 플로팅 된 박스와 그렇지 않은 박스는 겹쳐서 배치되기 때문.
- clear, flow-root 속성으로 해제할 수 있다.
- 컬럼을 배치하는 속성이 아니다.(실제로는 이렇게 사용하고 있지만..)
- 플로팅은 용도에 맞게 사용하고, 반드시 해제해야 한다.

##### 현업에서 가장 많이 사용하는 float 해제 방법

- ::after { clear: both }⭐

```css
<p class="container">
<span class="float">...</span>
...
::after
</p>
.container::after {
  content: '';
  display: block;
  clear: both;
}
```

#### float & display

- float 이 적용되면 display 속성이 block으로 바뀐다.

#### column layout

- float 대신 사용할 수 있다.
- columns : <'column-width'> || <'column-count'>
- break-inside : avoid // 한 박스를 도중에 자르지 않는다.

