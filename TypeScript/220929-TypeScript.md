# TODAY I LEARNED

## Learned

### @ts-check

JavaScript 파일에서 오류를 활성화하려면 // @ts-check를 .js 파일의 첫 번째 줄에 추가하여 TypeScript가 오류를 발생시키도록 합니다. TypeScript는 여러 오류를 제공할 수 있습니다.
이러한 오류를 무시하고 싶다면 // @ts-ignore 또는 // @ts-expect-error를 추가하여 특정 줄의 오류를 무시할 수 있습니다.
https://www.typescriptlang.org/docs/handbook/intro-to-js-ts.html#ts-check

### JSDoc Reference

JSDoc 주석을 사용하여 JavaScript 파일에 type 정보를 제공할 수 있습니다. (자바스크립트 파일에서 타입 정보를 제공할 수 있습니다.)
https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html

### 예시

```js
/**
* @param {string} p1 - A string param.
* @param {string=} p2 - An optional param (Google Closure syntax)
* @param {string} [p3] - Another optional param (JSDoc syntax).
* @param {string} [p4="test"] - An optional param with a default value
* @returns {string} This is the result
*/
function stringsStringStrings(p1, p2, p3, p4) {
// 코드...
}
```
https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html#param-and-returns
