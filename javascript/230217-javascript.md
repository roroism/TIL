# TODAY I LEARNED

## Learned

### Class

Class는 일종의 blueprint의 역할을 합니다.
```javascript
class User {
    constructor() {
        this.username = "Nicolas";
    }
    sayHello() {
        console.log("Hello");
    }
}
```

클래스는 안에 constructor를 가지고 있습니다.
constructor는 Class를 말 그대로 construct (구성) 한다는의미의 constructor입니다.

이 Class를 사용하려면 Class를 생성해주어야합니다. 생성한다. 구성(construct)한다.
```javascript
const sexyUser = new User();
```

위해서 sexyUser는 Class의 instance 입니다. instance 는 blueprint 를 토대로한 살아있는(메모리에 적재된) 상태입니다.
```javascript
console.log(sexyUser.username);
// 결과
// Nicolas

sexyUser.sayHello();
// 결과
// Hello
```

새로운 인스턴스들을 계속 생성할 수 있습니다.
```javascript
class User {
    constructor() {
        this.username = "Nicolas";
    }
    sayHello() {
        console.log("Hello, I'm Nicolas");
    }
}

const sexyUser = new User();
const uglyUser = new User();

sexyUser.sayHello();
uglyUser.sayHello();
// 결과
// Hello, I'm Nicolas
// Hello, I'm Nicolas
```

아래처럼 object를 이용할 수도 있지만, class하고 다른 점은, class는 constructor에 argument를 전달하여 매번 다른 값을 할당할 수 있습니다.
```javascript
// object인 경우
const baseObject = {
    username: "nicolas",
    sayHi: function () {
        console.log("hi nicolas");
    },
};

const sexyUser = baseObject;
const uglyUser = baseObject;

sexyUser.sayHello();
uglyUser.sayHello();
```

```javascript
// class인 경우
class SayName {
    constructor(name) {
        this.name = name;
    }
    SayNamefunc() {
        console.log(`My name is ${this.name}`);
    }
}

const callFunc = new SayName("Joey");
callFunc.SayNamefunc();
// 결과
// My name is Joey
```

Class는 기본적으로 일종의 object의 공장입니다.

