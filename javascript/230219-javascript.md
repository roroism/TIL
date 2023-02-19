# TODAY I LEARNED

## Learned

### this

```javascript
class Counter {
    constructor({ initialNumber = 0, counterId, plusId, minusId }) {
        this.count = initialNumber;
        this.counter = document.getElementById(counterId);
        this.counter.innerText = initialNumber;
        this.plusBtn = document.getElementById(plusId);
        this.minusBtn = document.getElementById(minusId);
        this.addEventListeners();
    }
    addEventListeners() {
        this.plusBtn.addEventListener("click", this.increase);
        this.minusBtn.addEventListener("click", this.decrease);
    }
    increase() {
        this.count = this.count + 1;
        this.repaintCount(); // error
    }
    decrease() {
        this.count = this.count - 1;
        this.repaintCount(); // error
    }
    repaintCount() {
        this.counter.innerText = this.count;
    }
}

new Counter({ counterId: "count", plusId: "add", minusId: "minus" });
```

위에서 this.repaintCount()의 this는 Counter Class를 가리키지 않고, HTMLButtonElement에서 repaintCount를 찾으려고 시도하고 없어서 error가 발생했습니다.

반대로 this.plusBtn.addEventListener("click", this.increase); 에서 this는 제대로 Counter Class를 가리킵니다.
```javascript
    // ...
    addEventListeners() {
        this.plusBtn.addEventListener("click", this.increase); // Counter Class를 가리킴.
        this.minusBtn.addEventListener("click", this.decrease);
    }
    increase() {
        this.count = this.count + 1; // increase 메소드 안에서의 this는 Button Element를 가리킴.
        this.repaintCount(); // error
    }
    // ...
```

addEventListener 처럼 this에 영향을 주는 경우, 아래처럼 arrow function을 사용하면 this의 문제가 해결됩니다.
```javascript
    // ...
    addEventListeners() {
        this.plusBtn.addEventListener("click", this.increase); // Counter Class를 가리킴.
        this.minusBtn.addEventListener("click", this.decrease);
    }
    // 화살표 함수로 수정..
    increase = () => {
        this.count = this.count + 1; // Counter Class를 가리킴.
        this.repaintCount(); // Counter Class를 가리킴.
    }
    // ...
```

#### 정리

eventListener 안에 event의 handler를 넣으면 event target을 가리키는 this를 가지게 됩니다.

즉, eventLister를 target에 add 할 때, 이 event의 handler는 this를 event target을 가르키게 합니다.

#### 활용

위처럼 class를 이용하게 되면 똑같은 기능이 필요한 부분에 같은 기능을 복제할 수 있습니다.

```javascript
// ...
new Counter({ counterId: "count", plusId: "add", minusId: "minus" });
new Counter({ counterId: "count2", plusId: "add2", minusId: "minus2", initialNumber: 66 });
```

