# TODAY I LEARNED

## Review

### Async

Async : 비동기성
- 컴퓨터는 딱히 순서가 필요없이 멀티태스킹을 할 수 있습니다.
- 그러나 문제는 어떤 작업이 언제 끝날지 알 수 없다는 점입니다.

#### Creating Promises

- Promise는 비동기 작업이 맞이할 미래의 완료 또는 실패를 나타냅니다.

```javascript
const amISexy = new Promise();
```

Promise를 만들 때는 실행할 수 있는 function을 넣어야합니다.
Promise를 호출할 때, 자바스크립트는 우리가 설정한 다른 function과(executor) 함께 이 Promise를 실행합니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	// 할 일.
});
```

```javascript
const amISexy = new Promise((resolve, reject) => {

});

console.log(amISexy);
// 결과
// Promise {<pending>}
```

pending 이라는 상태값이 출력되면서 함수가 끝나지 않고, 계속 대기중입니다.

이 Promise를 끝내기 위해서는 resolve function을 실행하는 것입니다.
그러면 Promise를 resolve할 것이고, Promise를 끝낼 것입니다. 그리고 값을 얻게 될 것입니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	setTimeout(resolve, 3000, "Yes you are");
});

console.log(amISexy);

setInterval(console.log, 1000, amISexy);
// 결과
// Promise {<pending>}		app.js:5
// Promise {<pending>}
// Promise {<pending>}
// Promise {<resolved>: "Yes you are"}
// Promise {<resolved>: "Yes you are"}
// ...
```

Promise의 핵심은 우리가 아직 모르는 value와 함께 작업할 수 있게 해준다는 것입니다.

#### then

자바스크립트에 promise 가 끝난 이후의 명령어를 전달하려면, 명령이 끝나고 나서 값을 돌려달라고 명령어를 내려야 합니다.

```javascript
const amISexy = new Promise((resolve, reject) => {
	setTimeout(resolve, 3000, "Yes you are");
});

amISexy.then(value => console.log(value));
```

