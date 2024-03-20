# TODAY I LEARNED

## Learned

### 자바스크립트 Console API

#### console.log

##### 콤마

- 콤마(,)를 통해 출력하고 싶은 여러개의 인자를 집어 넣을 수 있다.

```javascript
const a = 1;
const b = 'hello';
const c = true;

console.log(a); // 하나만 로그
console.log(a, b, c); // 여러 개를 동시에 로그
```

##### 출력 스타일링

- 콘솔 출력물 자체에 css를 적용할 수 가 있다.
- 위에서 본 문자열 포매팅 문법으로 스타일링을 뜻하는 기호는 `%c` 를 이용해, 콤마 다음으로 css 문법을 인라인으로 그대로 적어 주면 된다.

```javascript
console.log("This is %cMy stylish message", "color: yellow; font-style: italic; background-color: blue; padding: 2px");
```

- `%c` 를 여러 번 사용하여 각 문자마다 스타일링을 적용할 수 가 있다.

```javascript
console.log("Multiple styles: %cred %corange", "color: red", "color: orange", "Additional unformatted message");
```

##### 출력 스타일 모듈화

```javascript
let styles = [
    'background: linear-gradient(#D33106, #571402)', 
    'border: 1px solid #3E0E02',
    'color: white',
    'display: block',
    'text-shadow: 0 1px 0 rgba(0, 0, 0, 0.3)',
    'box-shadow: 0 1px 0 rgba(255, 255, 255, 0.4) inset, 0 5px 3px -5px rgba(0, 0, 0, 0.5), 0 -13px 5px -10px rgba(255, 255, 255, 0.4) inset',
    'line-height: 40px',
    'text-align: center',
    'font-weight: bold'
].join(';'); // 각 배열 인자들을 join 시켜 하나의 문자열로 치환하고 인자마다 끝에 ; 기호를 첨가해준다

console.log('%c a spicy log message ?', styles);
```

