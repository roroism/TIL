# TODAY I LEARNED

## Learned

### Logical OR Assignment

Logical Assignment Operators를 사용하면 우리들의 코드량을 줄여줍니다. 일종의 shortcut 역할을 해줍니다.

```javascript
const name = prompt("what is your name");

console.log(`Hello ${name}`);
```

위 코드를 실행해서 입력창에 값을 입력하면 콘솔에 출력될것입니다.
하지만 만약에 user가 cancel을 누르거나 아무것도 입력하지 않으면 null이 출력됩니다.
이 null 대신에 다른 값을 출력하고 싶다면?

```javascript
let name = prompt("what is your name");
if(!name) {
    name = "anonymous";
}

console.log(`Hello ${name}`);
```

위처럼 작성해 줄 수도 있겠지만,
대신에 logical or operator를 사용하여 표현할 수도 있습니다.

```javascript
let name = prompt("what is your name");
// if(!name) {
//     name = "anonymous";
// }
name ||= "anonymous";

console.log(`Hello ${name}`);
```

logical or operator는 변수가 falsy일 때 오른쪽의 값을 변수에 값을 넣을 수 있게 해줍니다.
변수에 텍스트, Array, Object가 오면 일어나지 않습니다.
* falsy : undefined, false, 빈 문자열, 0, null

### Logical AND Assignment

Logical AND Assignment는 OR 와 완전히 반대입니다.
변수에 value가 truthy라면 변수를 수정합니다. (덮어씁니다.)

예시 코드

```javascript
const user = {
    username: 'nico',
    password: 123
};

console.log(user);
// { username: 'nico', password: 123 }
```

위 코드에서 password의 value가 존재할 때,
콘솔에 공개적으로 password가 보이지 않게 보호하고 싶다면?

```javascript
const user = {
    username: 'nico',
    password: 123
};
if(user.password) {
    user.password = "[secret]";
}

console.log(user);
// { username: 'nico', password: '[secret]' }
```

Logical AND Assignment (&&=) 를 사용해서 바꾸면..

```javascript
const user = {
    username: 'nico',
    password: 123
};
// if(user.password) {
//     user.password = "[secret]";
// }
user.password &&= "[secret]";

console.log(user);
// { username: 'nico', password: '[secret]' }
```

추가 예시

```javascript
const user = {
    username: 'nico',
    password: 123
};

user.password &&= "[secret]";

user.name &&= "nico"; // user 객체에 name이 없기 때문에 동작하지 않습니다.
console.log(user);
// { username: 'nico', password: '[secret]' }

user.name ||= "nico"; // user 객체에 name이 없기 때문에 동작합니다.
console.log(user);
// { username: 'nico', password: '[secret]', name: 'nico' }
```

이처럼 적절한 상황에서 사용한다면 if나 else보다 훨씬 보기 좋습니다.

### Logical NULLISH Assignment

Logical NULLISH Assignment (??=) 은 Logical OR Assignment (||=) 하고 굉장히 비슷합니다.

```javascript
const user = {
    username: "nico",
    password: 123,
    isAdmin: ""
};

user.isAdmin ||= true;
user.isAdmin ??= true;
// 변수가 null이거나 undefined 일 때 true를 넣습니다.
// isAdmin이 undefined 일 경우 isAdmin은 true
// isAdmin이 null 일 경우 isAdmin은 true
// isAdmin이 "" 일 경우 isAdmin은 ""
// isAdmin이 0 일 경우 isAdmin은 0
// isAdmin이 false 일 경우 isAdmin은 false

console.log(user);
```

isAdmin이 falsy한 값(undefined, null, 0, "", false, NaN, -0) 이라면 ||=에 의하여 isAdmin에는 true가 출력될 것입니다.

||= 를 ??=로 바꾸면 ??=는 변수가 falsy인지 확인하는 것이 아니라. 오직 null이거나 undefined인 경우만 확인합니다.
즉, 오직 null이거나 undefined인 경우만 값을 할당합니다.

||=는 falsy 일 때 동작하고,
&&=는 truthy 일 때 동작하고,
??=는 null 또는 undefined 일 때 동작합니다.

