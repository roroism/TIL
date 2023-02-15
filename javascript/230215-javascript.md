# TODAY I LEARNED

## Learned

### Real world Promises

fetch는 promise를 return 합니다.
fetch는 무언가를 가지고 오는 역할을 합니다.

```javascript
fetch("https://yts.am/api/v2/list_movies.json")
    .then(response => {
        console.log(response);
        return response.json(); // response객체에 .json()을 실행하면 Promise로 반환합니다.
    })
    .then(json => console.log(json))
    .catch(e => console.log(`❌ ${e}`));
```

response 에는 Promise를 기반으로 하는 다양한 메서드가 있습니다. 이 메서드들을 사용하면 다양한 형태의 응답 본문을 처리할 수 있습니다. (예 : response.json() response.text() ...)

보통은 우리만의 Promise를 만들지는 않습니다. fetch를 사용한 것처럼 다른 사람이 만든 Promise를 사용하게됩니다.

