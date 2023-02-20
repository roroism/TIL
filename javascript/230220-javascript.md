# TODAY I LEARNED

## Learned

### Symbols

symbols은 새로운 Data Type 입니다. 매우 유니크한 Data Type입니다.
하나의 Symbol은 다른 Symbol들에 대해서 고유한 성질을 가집니다.

```javascript
const hello = Symbol();
const bye = Symbol();

console.log(hello === bye);
// 결과
// false
```

Symbol은 생성자에 한개의 인수 description을 가집니다.

```javascript
const hello = Symbol("hello");
const bye = Symbol("hello");

console.log(hello === bye);
// 결과
// false

console.log(hello);
// 결과
// Symbol(hello)
```

같은 description을 넣어도 이 둘은 다릅니다.
description에 넣는 값은 value가 아니며, 이를 Symbol 밖으로 꺼내서 사용할 방법은 없습니다.
단지, console.log에 출력할 description 일 뿐입니다.

#### Symbol의 활용 방법1 (Uniqueness)

```javascript
const superBig = {
    [Symbol("nico")]: {
        age: 12
    },
    [Symbol("nico")]: {
        age: 12
    }
};

console.log(superBig);
// 정상 출력
```

같은 key값을 추가하여 누군가 바꾸거나 반복하기를 원하지 않을 경우 등.. object의 key를 매우 고유하게 가지게 할 수 있습니다.

#### Symbol의 활용 방법2 (privacy)

```javascript
const superBig = {
    [Symbol("nico")]: {
        age: 12
    },
    [Symbol("nico")]: {
        age: 12
    }
};

console.log(Object.keys(superBig));
// []
```

key들이 출력되지 않습니다. 일반 속성을 하나 추가해보면..

```javascript
const superBig = {
    [Symbol("nico")]: {
        age: 12
    },
    [Symbol("nico")]: {
        age: 12
    },
    hello: "bye"
};

console.log(Object.keys(superBig));
// ["hello"]
```

위처럼, properties의 privacy를 원한다면 사용해 볼 수도 있습니다.

#### 정리

일반적으로 어플리케이션에서는 사용할 일이 많이 없고, library를 만들고 있는 사람들을 위한 것일 수 있다고 봅니다.
처음 symbols 의 아이디어는 javascript의 object에 private variable을 를 갖게 하는 것이었습니다.
결과적으로 unique하기는 하지만 그렇게 private하지는 않습니다.

