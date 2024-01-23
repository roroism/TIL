# TODAY I LEARNED

## Review (복습)

### 콜백

- 함수가 실행될 때, 인수로 들어가는 또 하나의 함수
- 함수도 또 하나의 데이터

예제 1
```javascript
const a = callback => {
  console.log('A');
  callback();
}
const b = () => {
  console.log('B');
}

a(b);

// 출력 결과
// A
// B
```

예제 2

```javascript
const sum = (a, b) => {
  setTimeout(() => {
    return a + b
  }, 1000);
}

console.log(sum(1, 2)); // undefined
console.log(sum(3, 7)); // undefined

// 위와 같은 경우에 의도한 대로 a + b가 반환되지 않고 undefined가 반환됩니다.
// 이런 경우 아래 처럼 콜백을 활용한다면..

const sum = (a, b, c) => {
  setTimeout(() => {
    c(a + b)
    return a + b
  }, 1000);
}

sum(1, 2, value => {
  console.log(value)
}) // 3
sum(3, 7, () => {
  console.log(value)
}) // 10
```

좀 더 유용한 예제
이미지를 load해서 출력하는 예제

```html
<div class="container">
  <h1>Loading...</h1>
</div>
```

```javascript
// https://www.gstatic.com/webp/gallery/4.jpg

const loadImage = (url, cb) => {
  const imgEl = document.createElement('img');
  imgEl.src = url;
  imgEl.addEventListener('load', () => {
    cb(imgEl);
  }); // 이미지의 load가 끝나면 콜백이 실행됨
}

const containerEl = document.querySelector('.container');
loadImage('https://www.gstatic.com/webp/gallery/4.jpg', (imgEl) => {
  containerEl.innerHTML = '';
  containerEl.append(imgEl);
}); // 두 번째 인수로 콜백을 추가함
```

