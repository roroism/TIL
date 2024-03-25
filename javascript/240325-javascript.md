# TODAY I LEARNED

## 복습

### 자식 노드 제거

#### removeChild()

- removeChild() 메서드는 부모 노드와 자식 노드의 관계를 끊으며, 관계가 끊어진 자식 노드를 반환합니다.

`const childNode = parentNode.removeChild(childNode);`

아래와 같이 반환 결과를 할당하는 변수가 없으면 관계가 끊어진 자식 노드를 메모리에 보관 후 JavaScript GC에 의해 제거됩니다.

`parentNode.removeChild(childNode);`

매개변수로 전달된 노드가 parentNode의 자식 노드가 아닌 경우 NotFoundError가 발생하며, null이 전달된 경우에는 TypeError가 발생합니다.

#### remove()

- 선택한 노드에서 remove() 메서드를 호출하면 해당 노드를 DOM 트리에서 바로 제거합니다.

```javascript
const ulNode = document.getElementById("ul-list");
ulNode.firstElementChild.remove();
```

#### replaceChildren()

- 선택한 노드의 모든 자식 노드를 지우고 싶은 경우 replaceChildren() 메서드를 호출합니다.

- replaceChildren() 메서드에 매개변수를 전달하지 않으면, 선택한 노드의 자식 노드를 빈 값으로 변경합니다.

```javascript
const ulNode = document.getElementById("ul-list");
ulNode.replaceChildren();
```

