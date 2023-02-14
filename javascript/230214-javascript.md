# TODAY I LEARNED

## Learned

### Promise.race()

Promise.race() 메소드는 Promise 객체를 반환합니다. 이 프로미스 객체는 iterable 안에 있는 프로미스 중에 가장 먼저 완료된 것의 결과값으로 그대로 이행하거나 거부합니다.

```javascript
const p1 = new Promise((resolve) => {
    setTimeout(resolve, 5000, "First");
});

const p2 = new Promise((resolve, reject) => {
    setTimeout(reject, 1000, "I hate JS");
});

const p3 = new Promise((resolve) => {
    setTimeout(resolve, 3000, "third");
});

const motherPromise = Promise.race([p1, p2, p3]);

motherPromise
    .then(values => console.log(values))
    .catch(err => console.log(err));
// 결과
// I hate JS
```

Promise.race() 는 Promise.all() 과 사용법은 같습니다.
Promise.race()의 다른 점은 위의 코드를 예시로.. Promise 3개 중에 하나라도 resolve 되거나 reject가 되면 결과가 나옵니다.
Promise.race()가 resolve 되어서 then으로 넘어가거나 reject 되어서 catch로 넘어가려면 p1, p2, p3 중 하나만 resolve 되거나 reject 되면 됩니다.
즉, 가장 빠른 것으로 결과를 정합니다.

Race는 어떤 것이든지 성공하거나, reject가 발생하지 않으면 resolve됩니다.

#### 사용

어느 것이 먼저 되는지 상관 없을 때 Race를 사용하면 됩니다.
