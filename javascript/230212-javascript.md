# TODAY I LEARNED

## Learned

### Async

인간은 순차적으로 한번에 하나씩 실행하지만, javascript는 동시에 여러가지 일을 할 수 있습니다.

### Creating Promises

Promise는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 나타냅니다.

```javascript
const amISexy = new Promise();
```

그래서 Promise를 만들 때는 실행할 수 있는 function을 넣어야합니다.
Promise를 호출할 때, 자바스크립트는 우리가 설정한 다른 function과(executor) 함께 이 Promise를 실행합니다.
```javascript
const amISexy = new Promise((resolve, reject) => {
	// 할 일.
});
```
resolve : "야, 이게 네 값이야. 자바스크립트로 돌아가."
reject : "야, 미안한데 에러가 있어."

```javascript
const amISexy = new Promise((resolve, reject) => {

});

console.log(amISexy);
// 결과
// Promise {<pending>}
```
pending이라는 상태값이 출력되면서 함수가 끝나지 않고, 계속 대기중입니다.


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
자바스크립트: "야, 이걸 해줘. 이건 바로 안 될 거야. 이걸 하고, 끝나면 다시 알려줘."

여기서 만약,
Promise가 API를 호출한다면 어떻게 할까요?
Promise가 파일 시스템에서 파일을 연다면?
Promise가 유저의 설정을 연다면?
로딩이 다 되면 그걸 다시 자바스크립트에게 돌려줘야 합니다.

