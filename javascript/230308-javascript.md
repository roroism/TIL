# TODAY I LEARNED

## Learned

### Static Fields and Methods

1. static 메소드와 필드.
2. private static 메소드와 필드.

#### static 메소드와 필드

static메소드는 인스턴스에 고정되지 않은 메소드입니다.

```javascript
class Counter {
    #count = 0;
    static description = "Count up to five.";
    static isMyChild(instance){
        return instance instanceof Counter;
    };
    
    plus() {
        if(this.#count === 5) {
            this.#reset();
        } else {
            this.#count++;
        }
    }
    
    #reset() {
        this.#count = 0;
    }
    
    get count() {
        return this.#count;
    }
}

const c = new Counter();
// c.description // 동작하지 않습니다.
console.log(c.description); // undefined

console.log(Counter.description); // Count up to five.

// c라는 인스턴스가 Counter클래스의 인스턴스인지 확인합니다.
console.log(Counter.isMyChild(c)); // true
```

static 메소드와 필드는 class 그 자체에 붙어있습니다. 클래스의 인스턴스로 접근할 수 없습니다.

#### private static 메소드와 필드

위에서 만든 static 필드와 메소드에 #을 붙여 private하게 만들수 있습니다.

```javascript
class Counter {
    #count = 0;
    static #description = "Count up to five.";
    static #isMyChild(instance){
        return instance instanceof Counter;
    };
    
    plus() {
        if(this.#count === 5) {
            this.#reset();
        } else {
            this.#count++;
        }
    }
    
    #reset() {
        this.#count = 0;
    }
    
    get count() {
        return this.#count;
    }
}

const c = new Counter();
console.log(c.description); // undefined
// console.log(Counter.#description); // error

// c라는 인스턴스가 Counter클래스의 인스턴스인지 확인합니다.
// console.log(Counter.isMyChild(c)); // error
```

