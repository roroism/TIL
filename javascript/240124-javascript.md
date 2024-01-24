# TODAY I LEARNED

## Learned

### 즉시실행함수(IIFE)

- 일반적으로 함수를 만들면서 호출하기 위해서 함수 이름을 부여합니다.
- 만약, 함수의 이름없이 바로 실행되기를 원한다면, 즉시실행함수 문법을 통해서 익명함수를 만들고 바로 실행할 수 있습니다.

**예시 코드**

```javascript
const a = 7;

const double = () => {
  console.log(a * 2);
}

double();

// 즉시 실행 함수
(() => {
  console.log(a * 2);
})();
```

**즉시실행함수의 다양한 패턴**

```javascript
// 아래 5개의 패턴 모두 같은 동작을 합니다.
;(() => {})()		// (F)()
;(function () {})()	// (F)()
;(function () {}())	// (F())
;!function () {}()	// !F()
;+function () {}()	// +F()
```

**또 다른 개념**

```javascript
;((a, b) => {
  console.log(a)
  console.log(b)
})(1, 2)

//console 출력 결과
// 1
// 2
```

- 두 번째 소괄호에 들어가는 각각의 데이터들을 즉시 실행하는 해당 함수에 매개변수로 전달해 줍니다.
- 이것을 사용하면 다양한 전역데이터들의 이름을 간소화할 수 있습니다.
- 예를 들면...

```javascript
;((a, b) => {
  console.log(a)
  console.log(b)
})(window, document)
```

- window객체와 document객체를 매개변수로 전달해주었지만, 즉시실행함수 내부에서는 a와 b라는, 해당 변수가 무엇을 의미하는지 전혀 유추할 수 없는 이름으로 바꿔서 사용할수 있습니다.
- 이 방식으로 해당하는 코드를 난독화할 수 있습니다.

