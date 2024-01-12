# TODAY I LEARNED

## Learned

### DOM(Document Object Model)

- HTML문서를 객체로 표현한 것 입니다.
- 그래서 JS에서 HTML을 제어할 수 있게 해줍니다.

#### DOM vs Element

- 노드(Node) : HTML 요소, 텍스트, 주석 등 모든 것을 의미
- 요소(Element) : HTML 요소를 의미
- 요소는 노드의 하위 개념

##### 예시 코드 1

```html
<body>
  <div class="parent">
    <!-- 주석 -->
    <div class="child">1</div>
    텍스트1
    <div class="child">2</div>
    텍스트2
  </div>
</body>
```

```javascript
// Node vs Element

// - 노드(Node) : HTML 요소, 텍스트, 주석 등 모든 것을 의미
// - 요소(Element) : HTML 요소를 의미

const parent = document.querySelector('.parent');

// 부모 요소의 모든 자식 노드 확인!
console.log(parent.childNodes);

// 부모 요소의 모든 자식 요소 확인!
console.log(parent.children);
```

##### 예시 코드 2

**요소를 console.log 로 출력했을 경우**
`console.log(parent)`
console.log 로 출력하면 div라는 요소가 출력됩니다.

**요소를 console.dir 로 출력했을 경우**
`console.dir(parent)`
console.dir 로 출력하면 하나의 객체 데이터로 출력됩니다.

