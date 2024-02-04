# TODAY I LEARNED

## 복습

### this

#### 예시 2

```javascript
const timer = {
  title: 'TIMER!',
  timeout() {
    console.log(this.title);
  }
}

timer.timeout(); // TIMER!
```

- 배운대로 일반함수에서의 this는 호출위치에서 정의되기 때문에 호출위치는 timeout함수가 호출된 timer.timeout() 이므로 this는 timer 객체가 되고 객체 안의 title을 출력하게 됩니다.

**setTimeout을 추가하면..**

```javascript
const timer = {
  title: 'TIMER!',
  timeout() {
    console.log(this.title); // TIMER!
    setTimeout(function () {
      console.log(this.title); // undefined
    }, 1000);
  }
}

timer.timeout(); // TIMER!
```

- setTimeout함수의 콜백으로 넣은 함수는 setTimeout 함수 내부 어딘가에서 호출이 됩니다.
- 일반함수에서의 this는 호출위치에서 정의되기 때문에 this는 setTimeout 함수 내부 어딘가에서 호출된 곳에서 정의됩니다.
- 참고로 우리는 setTimeout 함수의 내부 구조는 모르기 때문에 당연히 콜백으로 넣은 함수 this가 무엇을 가르키는지는 모릅니다. 그렇게 무엇인지 모르는 객체에서 title을 조회했기 때문에 'TIMER!' 가 출력될 수 없습니다.

**setTimeout 콜백 함수를 일반 함수에서 화살표 함수로 바꾸준다면..**

```javascript
const timer = {
  title: 'TIMER!',
  timeout() {
    console.log(this.title); // TIMER!
    setTimeout(() => {
      console.log(this.title); // TIMER!
    }, 1000);
  }
}

timer.timeout(); // TIMER!
```

- 배운대로 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의됩니다.
- 콜백 함수를 감싸고 있는 외부(상위) 범위는 timeout함수가 감싸고 있으므로 timeout이 됩니다.
- 이 때, timeout함수가 가지고 있는 this 키워드는 timer.timeout()에서 호출시점에 timer객체로 정의 되었으므로, 콜백으로 사용된 화살표 함수 안의 this는 timeout함수의 this 즉, timer 객체를 가리킵니다.

#### 정리

- this 키워드는 일반함수에서 화살표 함수에서 해석하는 방법이 다릅니다.
- 일반 함수의 this는 호출 위치에서 정의.
- 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의.

