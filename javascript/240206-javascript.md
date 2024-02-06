# TODAY I LEARNED

## 복습

### Promise

#### Promise 생성

```javascript
// Promise 객체의 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업을 수행

  if (/* 비동기 작업 수행 성공 */) {
    resolve('Success');
  }
  else { /* 비동기 작업 수행 실패 */
    reject('Failed');
  }
});
```

- Promise로 구현된 비동기 함수는 Promise 객체를 반환하며, 이로 구현된 비동기 함수를 호출하는 측에서 Promise 객체의 후속 처리 메서드(then, catch)를 통해 비동기 처리 결과 또는 에러메세지를 전달받아 처리한다. 
- 이를 통해 후속 처리 메서드를 체이닝 방식으로 호출이 가능하다.

#### Promise의 상태

- Pending(대기): 비동기 처리 로직이 아직 미완료인 상태
- Fulfilled(이행): 비동기 처리가 완료되어 promise가 결과 값을 반환해준 상태
- Rejected(실패): 비동기 처리가 실패하거나 오류가 발생한 상태

