# TODAY I LEARNED

## Review

### Promises

Async : 비동기성

#### Creating Promises

1. 생성

```javascript
const amISexy = new Promise();
```

2. Promise를 만들 때는 실행할 수 있는 function을 넣어야합니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	// 할 일.
});
```

3. Promise를 끝내기 위해서는 resolve function을 실행합니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	setTimeout(resolve, 3000, "Yes you are");
});
```

4. JavaScript에 promise 가 끝난 이후의 명령어를 전달하려면, 명령이 끝나고 나서 값을 돌려달라고 해야 합니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	setTimeout(resolve, 3000, "Yes you are");
});

amISexy.then(value => console.log(value));
```

5. Promise를 chaining으로 사용할 수 있습니다.(return을 작성하지 않으면 다음 then에 undefined가 전달됩니다.)

```javascript
const amIsexy = new Promise((resolve, reject) => {
    resolve(2);
});

amIsexy
    .then(number => {
        console.log(number * 2);
        return number * 2;
    })
    .then(othernumber => {
        console.log(othernumber * 2);
    });
// 결과
// 4
// 8
```

### Promise.all

- Promise.all이 다른 promise 들이 전부 진행 될 때까지 기다렸다가 진행됩니다.
- 그 중 하나라도 reject된다면 Promise.all도 reject 됩니다.

```javascript
const p1 = new Promise((resolve) => {
    setTimeout(resolve, 5000, "First");
});

const p2 = new Promise((resolve, reject) => {
    setTimeout(resolve, 1000, "second");
});

const p3 = new Promise((resolve) => {
    setTimeout(resolve, 3000, "third");
});

const motherPromise = Promise.all([p1, p2, p3]);

motherPromise.then(values => console.log("values"));
// 결과 (약 5초 뒤)
// ["First", "Second", "Third"]
```

