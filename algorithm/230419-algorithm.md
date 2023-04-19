# TODAY I LEARNED

## Learned

### JavaScript 입출력 문제 풀이

#### 혼자 힘으로 풀어보기

##### 문제 제목 : A+B

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.
첫째 줄에 A와 B가 주어진다. (0 < A, B < 10)

핵심 아이디어
- fs 모듈을 이용해 특정 파일에서 문자열을 읽어올 수 있다.

```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');
```

- 입력 받은 문자열 데이터를 정수로 변환해야 한다.

```javascript
let a = parseInt(line[0]);
```

#### 문제 제목 : 사칙연산

두 자연수 A와 B가 주어진다. 이때, A+B, A-B, A*B, A/B(몫), A%B(나머지)를 출력하는 프로그램을 작성하시오.
두 자연수 A와 B가 주어진다. (1 ≤ A, B ≤ 10,000)
첫째 줄에 A+B, 둘째 줄에 A-B, 셋째 줄에 A*B, 넷째 줄에 A/B, 다섯째 줄에 A%B를 출력한다.

핵심 아이디어
- JavaScript에서 나누기 연산(/)을 수행하면 실수 데이터가 반환될 수 있다.
- 따라서 몫을 구하기 위해서는 parseInt() 함수를 사용한다.

#### 문제 제목 : 곱셈

핵심 아이디어
- 문자열로 처리하면, 각 자릿수를 손쉽게 얻어 처리할 수 있다.

