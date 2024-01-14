# TODAY I LEARNED

## Learned

### Cookie, Storage

#### Cookie

- 도메인 단위(사이트 단위)로 저장
- 표준안 기준, 사이트당 최대 20개 및 4KB로 제한
- 영구 저장 불가능

##### Cookie에 값 할당

```javascript
document.cookie = 'a=1';

console.log(document.cookie);
```

##### Cookie의 값 누적

일반적으로 할당 연산자를 사용하면 새로운 값으로 덮어쓴다라고 생각할 수 있지만, Cookie에서는 값이 누적됩니다.

```javascript
document.cookie = 'a=1';
document.cookie = 'b=2';

console.log(document.cookie);
```

##### Cookie의 옵션

- domain : 유효 도메인 설정 (Cookie가 저장되는 사이트 주소 설정)
- path : 유효 경로 설정 (위의 해당 도메인의 하위 경로(상세 경로)도 설정할 수 있음)
- expires : 만료 날짜(UTC Date) 설정 (데이터가 유효할 수 있는 날짜를 지정할 수 있음)
- max-age : 만료 타이머(s) 설정 (데이터가 유효할 수 있는 시간을 지정할 수 있음)


- domain 옵션의 도메인과 현재 도메인 정보가 일치하지 않으면 해당 데이터는 저장되지 않음.
- path 옵션도 도메인의 상세 경로도 일치하지 않으면 저장되지 않음.

##### Cookie 옵션 추가하기

- 세미콜론(;)과 띄어쓰기로 구분하여 작성

**domain 옵션 지정하기**

```javascript
document.cookie = 'a=1; domain=localhost';
document.cookie = 'b=2';

console.log(document.cookie);
```

**path 옵션 지정하기**

```javascript
document.cookie = 'a=1; domain=localhost; path=/abc';
document.cookie = 'b=2';

console.log(document.cookie);
```

**max-age 옵션 지정하기**

```javascript
document.cookie = 'a=1; max-age=3'; // 3초를 지정함. 값이 할당되고 3초 뒤 이 정보는 만료됩니다.
document.cookie = 'b=2';

console.log(document.cookie);
```

**expires 옵션 지정하기**
국제 표준시(UTC)로 입력해야 합니다.

```javascript
document.cookie = `a=1; max-age=${1 * 60 * 60 * 24}`; // 하루를 만료시간으로 지정함
document.cookie = `b=2; expires=${new Date(2022, 11, 16).toUTCString()}`; // 2022년 12월 16일 지정함

console.log(document.cookie);
```

만료 시간을 따로 설정하지 않는다면?
- 브라우저가 종료되면 해당 쿠키도 만료됩니다.
- 개발자 도구에서 '만료 시간' 대신 '세션'이라는 값으로 표현됩니다.

##### Cookie값 추출하는 함수 만들기

```javascript
document.cookie = `b=2`;
document.cookie = `a=3`;
console.log(document.cookie); // a=2; a=3

function getCookie(name) {
  const cookie = document.cookie
  .split('; ') // ['b=2', 'a=3']
  .find(cookie => cookie.split('=')[0] === name); // a=3
  
  return cookie ? cookie.split('=')[1] : null; // 3
}

console.log(getCookie('a')); // 3
```

##### Cookie 정리

Cookie는 정보를 만료날짜와 시간을 설정하여 관리할 수 있다는 장점이 있지만,
저장 갯수와 용량 제한이 있기 때문에 일반적인 데이터를 브라우저에 저장하는 용도로는 적합하지 않습니다.

#### Storage(스토리지)

- Cookie와 마찬가지로 도메인 단위로 저장
- 5MB 제한
- 세션 혹은 영구 저장 가능

Storage에는 두가지 방식이 있다.
- sessionStorage : 브라우저 세션이 유지되는 동안에만 데이터 저장
- localStorage : 따로 제거하지 않으면 영구적으로 데이터 저장


제공하는 옵션
- .getItem() : 데이터 조회
- .setItem() : 데이터 추가
- .removeItem() : 데이터 제거
- .clear() : 스토리지 초기화

##### 예시 코드

```javascript
localStorage.setItem('a', 'Hello world!');
localStorage.setItem('b', { x: 1, y: 2 });
localStorage.setItem('c', 123);

console.log(localStorage.getItem('a'));
console.log(localStorage.getItem('b'));
console.log(localStorage.getItem('c'));
```

storage에는 항상 문자 형태로 저장됩니다.
그래서 객체 데이터는 제대로 저장되지 않고, 숫자는 문자로 바뀌어 저장됩니다.

##### 모든 데이터는 JSON화하여 저장

JSON.stringify함수를 사용하여 json 형태로 바꾸어 저장합니다.

```javascript
localStorage.setItem('a', JSON.stringify('Hello world!')); // x
localStorage.setItem('b', JSON.stringify({ x: 1, y: 2 })); // 객체를 json화하여 저장
localStorage.setItem('c', JSON.stringify(123); // 숫자도 json화하여 저장

console.log(JSON.parse(localStorage.getItem('a')));
console.log(JSON.parse(localStorage.getItem('b'))); // 객체로 가져옴
console.log(JSON.parse(localStorage.getItem('c'))); // 숫자로 가져옴
```

Storage를 사용할 때, JSON.stringify와 JSON.parse를 항상 사용해주는 것을 권장합니다.

##### 정리

- 임시로 사용자가 브라우저를 사용할 때만 쓰이는 데이터들은 sessionStorage로 관리하고, 매번 사용자가 페이지에 들어와서 계속 저장하고 사용해야 하는 데이터는 localStorage를 사용하면 됩니다.
- Storage는 만료(시간 만료)라는 개념이 없습니다.
- 시간이 지나서 데이터가 꼭 제거 되어야 한다면 storage가 아닌 cookie를 사용할 수 있습니다.

