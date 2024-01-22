# TODAY I LEARNED

## Learned

### 호출 스케줄링

#### setTimeout

```html
<h1>Hello world!</h1>
```

```javascript
const hello = () => {
  console.log('Hello~');
}

const timeout = setTimeout(hello, 2000);
const h1El = document.querySelector('h1');
h1El.addEventListener('click', () => {
  console.log('Clear!');
  clearTimeout(timeout);
});
```

#### setInterval

```javascript
const hello = () => {
  console.log('Hello~');
}

const timeout = setInterval(hello, 2000);
const h1El = document.querySelector('h1');
h1El.addEventListener('click', () => {
  console.log('Clear!');
  clearInterval(timeout);
});
```

