# TODAY I LEARNED

## Learned

### nextElementSibling

- Element.nextElementSibling는 DOM(Document Object Model)에서 사용되는 프로퍼티 중 하나입니다.
- 현재 요소의 다음 형제 요소를 나타냅니다.
-  형제 요소란 같은 부모 요소를 공유하는 다른 요소를 말합니다.
- 다음 형제 요소가 없는 경우 null을 반환합니다.

```html
<ul>
  <li>사과</li>
  <li id="selected">바나나</li>
  <li>체리</li>
  <li>딸기</li>
</ul>
```

```javascript
var selectedElement = document.getElementById("selected");
var nextElement = selectedElement.nextElementSibling;

console.log(nextElement.textContent); // 체리
```

