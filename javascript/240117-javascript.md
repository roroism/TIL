# TODAY I LEARNED

## Learned

### History

브라우저 히스토리(세션 기록) 정보를 반환하거나 제어합니다.

#### 예제2

```html
<!-- ... -->
<body>
  <a href="#hello1">Hello 1</a>
  <a href="#hello2">Hello 2</a>
  <a href="#hello3">Hello 3</a>
</body>
</html>
```

```javascript
console.log(history);
```

**.pushState()**

- .pushState(상태, 제목, 주소) : 히스토리에 상태 및 주소를 추가
- 모든 브라우저(Safari 제외)는 '제목' 옵션을 무시합니다.
- 하나의 새로운 히스토리를 기록합니다.
- location의 assign의 메소드 처럼 페이지를 새로고침하지 않습니다.

**.replaceState()**

- .replaceState(상태, 제목, 주소) : 현재 히스토리의 상태 및 주소를 교체
- pushState와 비슷하지만, 현재페이지에 대한 히스토리 정보를 제거하고 추가합니다. 즉 교체 됩니다.

