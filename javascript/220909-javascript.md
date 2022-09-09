# TODAY I LEANRED

## Learned

### Number()와 parseInt()의 차이

두 함수 모두 문자열 타입의 숫자를 `Number` 타입으로 바꿔줍니다.

차이점은 `parseInt()` 은 문자열을 파싱해서(숫자 아닌 문자가 섞여있어도) 숫자를 찾는 기능을 가지고 있고, 
`Number()`는 숫자로만 이루어져 있는 문자열타입 숫자만을 `number` 타입으로 바꿔줍니다.

문자 `'1'` 을 변환시도
```js
var strNum = "1";
console.log("parseInt : " + parseInt(strNum)); // 1
console.log("Number : " + Number(strNum)); // 1
```

문자 `'01'` 을 변환시도

```js
var strNum = "01";
console.log("parseInt : " + parseInt(strNum)); // 1
console.log("Number : " + Number(strNum)); // 1
```

문자 `'2016년도'` 을 변환시도

```js
var strNum = "2016년도";
console.log("parseInt : " + parseInt(strNum)); // 2016
console.log("Number : " + Number(strNum)); // NaN
```
parseInt() 는 정확히 숫자만을 골라 파싱하지만, Number() 는 실패했습니다.

문자 `'제10회'` 을 변환시도

```js
var strNum = "제10회";
console.log("parseInt : " + parseInt(strNum)); // NaN
console.log("Number : " + Number(strNum)); // NaN
```

문자열로 시작하면 parseInt() 도 파싱에 실패하여 NaN 을 출력합니다.

문자 `'10.123'` 을 변환시도

```js
var strNum = "10.123";
console.log("parseInt : " + parseInt(strNum)); // 10
console.log("Number : " + Number(strNum)); // 10.123
```

parseInt() 는 소수점은 출력하지 못합니다. 대신 소수까지 출력할 수 있는 parseFloat() 함수가 따로 존재합니다.

```js
var strNum = "10.123";
console.log("parseInt : " + parseInt(strNum)); // 10
console.log("parseFloat : " + parseFloat(strNum)); // 10.123
console.log("Number : " + Number(strNum)); // 10.123
```
