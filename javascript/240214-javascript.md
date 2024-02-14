# TODAY I LEARNED

## 복습

### append vs appendChild

- append와 appendChild 메서드는 모두 부모 노드에 자식 노드를 추가하는 메서드입니다.

#### append

1. 노드 객체(Node object)를 전달할 수 있습니다.
2. DOMString(text)도 전달할 수 있습니다.
3. 한번에 여러 개의 자식 요소를 설정할 수 있습니다.

```javascript
// 노드 객체 사용 예시
const parent = document.createElement('div');
const child = document.createElement('p');

parent.append(child);
// 결과
// <div><p></p></div>

// 문자열(DOMString) 사용 예시
// DOMString 삽입
const parent = document.createElement('div');
parent.append('append 예시');

// 결과
// <div>append 예시</div>

// 여러 개의 자식 요소 사용 예시
const div = document.createElement('div');
const span = document.createElement('span');
const p = document.createElement('p');

document.body.append(div, 'hello', span, p);

// result
// <body>
//   <div></div>
//   hello
//   <span></span>
//   <p></p>
// </body>
```

#### appendChild

1. 오직 노드 객체(Node object)만 전달할 수 있습니다.
2. 한번에 오직 하나의 자식 요소만 추가할 수 있습니다.

```javascript
// 노드 객체 사용 예시

// Node object 삽입
const parent = document.createElement('div');
const child = document.createElement('p');
parent.appendChild(child);

// <div><p></p></div>

// 문자열(DOMString)을 넣을 경우 에러 발생 예시
// DOMString 삽입
const parent = document.createElement('div');

parent.appendChild('텍스트');
// Uncaught TypeError: Failed to execute 'appendChild' on 'Node': parameter 1 is not of type 'Node'
```

