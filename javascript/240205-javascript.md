# TODAY I LEARNED

## 복습

### Promise.allSettled

- Promise.allSettled() 메서드는 주어진 모든 프로미스를 이행하거나 거부한 후, 각 프로미스에 대한 결과를 나타내는 객체 배열을 반환합니다.

- 일반적으로 서로의 성공 여부에 관련 없는 여러 비동기 작업을 수행해야 하거나, 항상 각 프로미스의 실행 결과를 알고 싶을 때 사용합니다.

- 그에 비해, Promise.all()이 반환한 프로미스는 서로 연관된 작업을 수행하거나, 하나라도 거부 당했을 때 즉시 거부하고 싶을 때 적합합니다.

```javascript
const values = await Promise.allSettled([
  Promise.resolve(33),
  new Promise((resolve) => setTimeout(() => resolve(66), 0)),
  99,
  Promise.reject(new Error("an error")),
]);
console.log(values);

// [
//   {status: "fulfilled", value: 33},
//   {status: "fulfilled", value: 66},
//   {status: "fulfilled", value: 99},
//   {status: "rejected",  reason: Error: an error}
// ]
```

