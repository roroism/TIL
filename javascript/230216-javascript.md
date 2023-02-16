# TODAY I LEARNED

## Learned

### try catch finally

Async Await에서의 catch하는 방법.

#### try catch

```javascript
// 기존
const getMoviesAsync = async () => {
    const response = await fetch("https://yts.mx/api/v2/list_movies.json");
    console.log(response);
    const json = await response.json();
    console.log(json);
};

getMoviesAsync();

// try catch 추가
const getMoviesAsync = async () => {
    try {
        const response = await fetch("https://yts.mx/api/v2/list_movies.json");
        const json = await response.json();
        console.log(json);
    } catch(e) {
        console.log(`❌ ${e}`);
    }    
};

getMoviesAsync();

// finally 추가
const getMoviesAsync = async () => {
    try {
        const response = await fetch("https://yts.mx/api/v2/list_movies.json");
        const json = await response.json();
        console.log(json);
    } catch(e) {
        console.log(`❌ ${e}`);
    } finally {
        console.log("We are done!");
    }  
};

getMoviesAsync();
```

throw Error를 추가해본다면?
```javascript
// throw Error를 추가해 본다면?
const getMoviesAsync = async () => {
    try {
        const response = await fetch("https://yts.mx/api/v2/list_movies.json");
        const json = await response.json();
        throw Error("Im hungry");
    } catch(e) {
        console.log(`❌ ${e}`);
    } finally {
        console.log("We are done!");
    }  
};

getMoviesAsync();
// 결과
// ❌ Error: Im hungry
// We are done!
```
throw로 던진 error message를 catch의 인수로 받습니다. 그리고
try catch는 try catch 블록안에만 있다면 await 밖에 있는 error까지 잡습니다.

#### 6 Reasons Why JavaScript Async/Await Blows Promises Away

참고 사이트
https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9

### Parallel Async Await

코드 예
```javascript
const getMoviesAsync = async () => {
    try {
        const [moviesResponse, upcomingResponse] = await Promise.all([
          fetch("https://yts.mx/api/v2/list_movies.json"),
          fetch("https://yts.mx/api/v2/movie_suggestions.json?movie_id=100"),
        ]);

        const [movies, upcoming] = await Promise.all([
          moviesResponse.json(),
          upcomingResponse.json(),
        ]);

        console.log(movies, upcoming);
    } catch (e) {
        console.log(e);
    } finally {
        console.log("we are done");
    }
};

getMoviesAsync();
```

