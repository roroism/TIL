# TODAY I LEARNED

## Review

### 코딩 테스트를 위한 JavaScript 핵심 문법 알아보기

#### fs 모듈

- 기능 : 전체 텍스트를 읽어 온 뒤에, 줄바꿈 기호를 기준으로 구분하여 리스트로 변환하기

```javascript
// readline 모듈보다는 fs를 이용해 파일 전체를 읽어 들여 처리하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');
console.log(input);
```

#### readline 모듈

- 기능 : 한 줄씩 입력받아서, 처리하여 정답을 출력할 때는 readline 모듈을 사용할 수 있다.

```javascript
const rl = require('readline').createInterface({
    input: process.stdin,
    output: process.stdout
});

let input = [];
rl.on('line', function(line) {
    // 콘솔 입력 창에서 줄바꿈(Enter)를 입력할 때마다 호출
    input.push(line);
}).on('close', function() {
    // 콘솔 입력 창에서 Ctrl + C 혹은 Ctrl + D를 입력하면 호출(입력의 종료)
    console.log(input);
    process.exit();
})
```

#### 배열 초기화

- 알고리즘 문제를 풀 때 자주 사용되는 배열 초기화 방식은 다음과 같다.

```javascript
// 직접 값을 설정하여 초기화
let arr = [8, 1, 4, 5, 7];
```

```javascript
// 길이가 5이고 모든 원소의 값이 0인 배열 초기화
let arr = new Array(5).fill(0);
```

