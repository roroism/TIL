# TODAY I LEARNED

## Learned

### Proxies

Proxy 객체를 사용하면 한 객체에 대한 기본 작업을 가로채고 재정의하는 프록시를 만들 수 있습니다.

proxy를 filter처럼 생각해볼 수 있습니다.
```javascript
const userObj = {
    username: "nico",
    age: 12,
    password: 1234
}

const userFilter = {};

// userFilter를 통해서 userObj를 filter할 수 있습니다.
const filteredUser = new Proxy(userObj, userFilter);
```

proxy는 두 개의 input을 가지고 있습니다.
하나는 target (filter를 하고 싶은 object),
다른 하나는 handle (target의 필터)
```javascript
filteredUser.age // 출력 : 12
filteredUser.password // 출력 : 1234
```
위처럼 filteredUser에서 userObj의 값을 가져올 수 있습니다. 참고로 userFilter는 현재 빈 객체 입니다.

기본적으로 filteredUser를 호출하면 userFilter가 호출되고 그 다음에 userObject의 value가 반환되거나 반환되지 않을 수 있습니다.

```javascript
const userObj = {
    username: "nico",
    age: 12,
    password: 1234
}

const userFilter = {
    get: () => {
        console.log("Somebody is getting something");
        // return "NOTHING"; // return도 가능.
    }
    set: () => {
        console.log("Somebody wrote something");
    }
};

// userFilter를 통해서 userObj를 filter할 수 있습니다.
const filteredUser = new Proxy(userObj, userFilter);

filteredUser.password // Somebody is getting something
filteredUser.active = true // Somebody wrote something
```
위에서 get, set 함수이름은 임의로 정한 것이 아닌 정해놓은 함수입니다. (proxy 문서 참고)
filter 객체 안의 get, set 등과 같은 함수들을 trap이라고 부릅니다.

filteredUser.password 를 실행하면 proxy는 trap을 호출하고, get이 실행됩니다.
filteredUser.active 라는 property를 새로 만들고 true를 할당하면,(filteredUser.active = true) set이 실행됩니다.

정리하면..

1. Proxy를 만들고 Proxy에게 targetObj와 userFilter를 인수로 입력합니다.
2. userFilter는 몇 가지 properties를 가집니다. (get 이나 set 등)
3. Proxy는 userObj의 이벤트를 가로채서 그 이벤트의 행위를 못하게 하고, trap으로 정의한 것을 실행합니다.

#### trap들의 argument

```javascript
const userObj = {
    username: "nico",
    age: 12,
    password: 1234
}

const userFilter = {
    get: (target, prop, receiver) => {
        console.log(target); // userObj // object출력 여기서는 userObj
        console.log(prop); // age // 속성이름출력 여기서는 호출한 age
        console.log(receiver); // proxy를 출력합니다.
    }
    set: () => {
        console.log("Somebody wrote something");
    }
};

const filteredUser = new Proxy(userObj, userFilter);

filteredUser.age;
```

1. target argument
실제 object가 출력됩니다.
2. prop argument
user가 요청한 property data(속성 이름)을 logging합니다.
3. receiver argument
proxy를 출력합니다.

#### argument 사용

1. 사용 예1

```javascript
const userFilter = {
    get: (target, prop, receiver) => {
        return target[prop];
    }
};

const filteredUser = new Proxy(userObj, userFilter);

filteredUser.age; // 12
```

만약에 누군가 age를 호출한다면 target[prop] 으로 age를 반환하게 할 수 있습니다.

2. 사용 예2

```javascript
const userFilter = {
    get: (target, prop, receiver) => {
        return prop === "password" ? `${"*".repeat(5)}` : target[prop];
    }
};

const filteredUser = new Proxy(userObj, userFilter);

filteredUser.age; // 12
```

