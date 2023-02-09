# TODAY I LEARNED

## Learned

### Rest + Spread + Destructure Magic

#### rest의 훌륭한 예시

1. 특정 속성값을 제외시키기

```javascript
const user = {
	name: "nico",
	age: 24,
	password: 12345,
};

// user["password"] = null;
// console.log(user); // password 값을 null로 변경.

const killPassword = ({ password, ...rest }) => rest;
const cleanUser = killPassword(user);
console.log(cleanUser); // password 속성 자체를 제거.
// 출력
// {name: "nico", age: 24}
// object로 리턴됐다는 점에 유의
```

2. 기본값 설정하기

```javascript
const user = {
	name: "nico",
	age: 24,
	password: 12345,
};

const setCountry = ({country = "KR", ...rest}) => ({ country, ...rest });

console.log(setCountry(user));
// 출력
// { country: "KR", name: "nico", age: 24, password: 12345 }
```

3. 속성명 바꾸기(rename property)

```javascript
const user = {
	NAME: "nico",
	age: 24,
	password: 12345,
};

const rename = ({ NAME: name, ...rest }) => ({name, ...rest})

console.log(rename(user));
// 출력
// { name: "nico", age: 24, password: 12345 }
```

