# TODAY I LEARNED

## 복습

### Node vs Element

**DOM(Document Object Model)**

- HTML문서를 객체로 표현한 것 입니다.
- 그래서 JS에서 HTML을 제어할 수 있게 해줍니다.

**DOM API 사용 예**

```javascript
const element = document.querySelector('h1');
console.log(element.textContent);
```

#### DOM vs Element

- 노드(Node) : HTML 요소, 텍스트, 주석 등 **모든 것을 의미**
- 요소(Element) : HTML 요소를 의미
- 요소(Element)는 노드(Node)의 하위 개념

##### 예시 코드 1 (childNodes와 children)

index.html

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

main.js

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

**결과**

childNodes는 모든 html의 구조를(Nodes들을) 보여주고, children은 요소(Element)만을 보여줍니다.

##### 예시 코드 2 (Div 요소의 prototype을 확인해 보기)

**요소를 console.log로 출력했을 경우**
- console.log 로 출력하면 div라는 요소가 출력됩니다.

**요소를 console.dir 로 출력했을 경우**
- 객체로 출력을 하고 싶다면 console.dir을 사용하면 됩니다.
- Prototype을 타고타고 내려가다 보면 HTMLDivElement -> HTMLElement -> Element -> Node 순으로 상속받은 상위 객체로 올라 갈 수 있습니다.
- Node 아래에 Element가 포함되어 있다는 것을 확인할 수 있습니다. 즉, 요소(Element)는 노드(Node)의 하위 개념입니다.

##### 예시 코드 3 (Class와 Element의 `__proto__` 확인해보기)

```javascript
class N {}
class E extends N {}

console.dir(E); // class E
console.dir(N); // class N
console.dir(E.__proto__); // class N

console.dir(Element); // f Element()
console.dir(Node); // f Node()
console.dir(Element.__proto__); // f Node()
```

- console.dir(E)의 console 결과. Prototype에 class N을 확인할 수 있습니다. 이것으로 class E는 class N을 상속받고 있다는 것을 알 수 있습니다.

- javascript에서 상위 클래스를 확인하고 싶을 땐, `.__proto__`을 확인하면 됩니다.
- `.__proto__`을 사용하면 `[[prototype]]`의 내용을 확인할 수 있습니다.
- `__proto__` 의 내용을 보기위해 console로 출력해 보았지만, 우리가 일반적으로 사용하라고 만든 속성은 아닙니다.
- 마찬가지로 Element의 `__proto__` 을 화인해보면 그 상위 개념인 Node가 출력되는 것을 확인할 수 있습니다.

##### 정리

- 노드(Node)가 요소(Element)보다 더 상위개념입니다.
- 이 개념을 알아야 하는 이유는 DOM API의 여러가지 속성과 메소드들이 어떤 것은 Node라는 개념에서 실행이되고, 어떤 것은 Element에서 실행이 되기 때문입니다.
- 요소(Element)에서 실행되는 것은 텍스트나 주석에서는 동작되지 않지만, 노드(Node)에서 실행되는 속성이나 메소드들은 노드가 요소보다 더 상위개념이기 때문에 요소에서도 그대로 사용할 수 있습니다.

