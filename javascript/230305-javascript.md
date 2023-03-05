# TODAY I LEARNED

## Learned

### Numeric Separators

단위 수를 알아보기 쉽게 _ 를 사용하여 구분하여 표현할 수 있습니다.
가끔 진짜 큰 숫자를 쓸 때 유용합니다.

```javascript
const allTheMoney = 11_000_000_000_000_000;
// _ 를 사용해서 숫자를 나누면 훨씬 쉽게 셀 수 있습니다.

console.log(allTheMoney);
// 출력
// 11000000000000000
// 숫자를 읽기 쉽게 바꿔줄뿐 값을 변경시키지는 않습니다.
```

작성자 입장에서 편리한 기능입니다. 실제로 값에 영향을 주지는 않습니다.
float에서도 동작합니다.(소수점)
작성자가 원하는 곳 아무대나 넣어서 사용할 수 있습니다. (예 : 1_1_0_0_0_1.345)
단, 연속으로 _ 를 2개 이상 사용하면 안됩니다.

### Promise.any

Promise.any는 매우 흥미롭습니다. 그 전에
먼저, Promise.all 을 먼저 알아봅니다.

```javascript
Promise.all([p1, p2, p3]).then();
```

위 코드에서 Promise.all은 p1, p2, p3 가 모두 다 끝날 때까지 기다립니다.
p1, p2, p3가 끝난 뒤에야 .then으로 가서 Promise.all이 끝납니다.

Promise.any는 다릅니다.

```javascript
Promise.any([p1, p2, p3]).then();
```

Promise.any는 p1, p2, p3 중 어느 하나가 끝나기를 기다립니다.
이것들 중 어느 것이라도 끝이 나면 다음으로 넘어갑니다. 예를 들어 p2가 먼저 끝났다면, p1과 p3를 기다리지 않고 바로 then으로 넘어갑니다.
만약, 이들 중 아무것도 끝나지 않았다면 aggregate error가 발생합니다.

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(reject, 1000, "quick");
});

const p2 = new Promise((resolve, reject) => {
    setTimeout(reject, 5000, "quick");
});

Promise.any([p1, p2]).then(console.log);
// then은 실행되지 않습니다. 그 대신 에러가 발생합니다.
// Problems : All Promises were rejected
```

이번에는 catch로 error를 잡아봅니다.

```javascript
const p1 = new Promise((resolve, reject) => {
    setTimeout(reject, 1000, "quick");
});

const p2 = new Promise((resolve, reject) => {
    setTimeout(reject, 5000, "quick");
});

Promise.any([p1, p2]).then(console.log).catch(console.log);
// 2개가 다 실행되어 reject가 된 후, catch가 실행됩니다.
// AggregateError : All promises were rejected
```

위 에러 메세지는 전체 promise 포함하여 하나의 에러 메세지로 나타냈지만,
error 메세지를 직접 출력해보면 각각의 Promise 별로 에러상태를 배열로 구분하여 출력해줍니다.

```javascript
Promise.any([p1, p2])
.then(console.log)
.catch(e => {
    console.log(e.errors);
});
// ["quick", "slow"]
```

all은 모두가 끝나길 기다리고,
any는 하나만 끝나길 기다리고 나머지는 신경쓰지 않습니다.

### replaceAll

replaceAll은 string 안에 있는 모든 표적을 대체할 수 있습니다.
replaceAll은 원래 값을 변화시키지 않고 새로운 string을 return합니다.

첫번째 argument는 바꾸고 싶은 것, 두번째 argument는 어떤 걸로 바꿀지 넣어주면 됩니다.

```javascript
const name = "Nicolaso";

const newName = name.replaceAll("o", "❤");

console.log(name, newName);
// Nicolaso Nic❤las❤
```

