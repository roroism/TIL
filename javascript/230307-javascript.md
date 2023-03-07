# TODAY I LEARNED

## Learned

### Class Field Declarations

JavaScript는 진짜 객체 지향 프로그래밍 언어들이 지원하는 모든 특징을 가지고 있지는 않습니다.
하지만 ECMA2022로 오면서 점점 가까워지고 있어서, 이전에 사용하지 못했던 객체 지향 프로그래밍 언어들이 가진 특징들을 더 많이 쓸 수 있게 됐습니다.

이번에는 Class에서의 필드 선언에 대한 것부터 알아보겠습니다.
먼저 예시코드로 Counter class를 만들어보겠습니다.

```javascript
class Counter {
    constructor() {
        this.count = 0;
    }
    plus() {
        this.count++;
    }
}
```

위에서처럼 변수를 초기화 하려면 constructor를 작성해야 했습니다.
Class Field Declarations를 사용하면 constructor를 작성하지 않고도 바로 필드에서 초기화 할 수 있습니다.

```javascript
class Counter {
    count = 0;
//    constructor() {
//        this.count = 0;
//    }
    plus() {
        this.count++;
    }
}
```

코드는 더 깔끔해졌고, 결과는 똑같이 나옵니다.

### Private Methods and Fields

Private 메소드와 필드에 대해 알아보겠습니다.
이는 마치 Java나 C#, TypeScript 에서 코딩하는 느낌을 줄 것입니다.
지금까지의 JavaScript에서는 Private Methods and Fields는 없었습니다.

Private 메소드와 필드를 쓰는 이유는 'Class를 보호하기 위해서' 입니다.

`#`를 앞에 붙여서 필드나 속성, 메소드를 private로 만들 수 있습니다.

#### Private Fields

```javascript
class Counter {
    count = 0;
    plus() {
        this.count++;
    }
}

const c = new Counter();
c.plus(); // 1증가
c.plus(); // 1증가
c.count = 100000; // 누군가 악의적으로 값을 바꾼다면?
console.log(c.count); // 100000
```

위 코드처럼 원하지않는 상황이 발생할 수도 있습니다. count 값을 보호해야 하는 상황입니다.
이 때, private하게 바꾸어 클래스 내부에서만 count 값을 수정할수 있고, 클래스 밖에서는 수정할 수 없게 합니다.
count를 private 필드로 만드려면 변수명 앞에 #을 붙입니다.

```javascript
class Counter {
    #count = 0;
    plus() {
        this.#count++;
    }
}

const c = new Counter();
c.plus(); // 1증가
c.plus(); // 1증가
// c.#count = 100000; // error 발생
console.log(c.#count); // 2
```

#### Private Methods

Private 메소드도 만들 수 있습니다.

```javascript
class Counter {
    #count = 0;
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
c.plus(); // 1증가
c.plus(); // 1증가
c.plus(); // 1증가
c.plus(); // 1증가
c.plus(); // 1증가
// c.#reset(); // private 메소드 이므로 error 발생.
console.log(c.count); // 5

c.plus(); // 1증가
console.log(c.count); // 0
```

Private Fields와 마찬가지로 Private Methods도 오직 클래스안에서만 접근할 수 있습니다.
위 코드에서 reset 함수는 외부로 부터 보호됩니다.
클래스 안에서만 사용하게 되는 메소드는 private하게 만들어주고, 클래스 외부에서 값을 불러올 수 있게 public으로 getter 함수를 만들어줍니다.

참고로 메소드 앞에 get키워드를 사용하면 javascript에게 getter함수로 인지하게 할 수 있습니다.

1. get 키워드를 사용할 경우.

```javascript
// ...
    #count = 0;
// ...
    get count() {
        return this.#count;
    }
// ...

console.log(c.count);
```

2. get 키워드를 사용하지 않을 경우.

```javascript
// ...
    #count = 0;
// ...
    count() {
        return this.#count;
    }
// ...

console.log(c.count());
```

