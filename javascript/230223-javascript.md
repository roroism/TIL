# TODAY I LEARNED

## Learned

### Generators

Generator는 iterable한 객체를 반환합니다. iterable 하다는 뜻은 배열의 보다 일반적인 의미로, Array type을 포함하여 string, nodeList 등 유사 배열 객체 등을 포함하며, for ...of 문법을 사용할 수 있다는 특징이 있습니다.

Generators는 기본적으로 pause할 수 있는 함수입니다.
Generators를 사용하기 위해서는 몇가지 규칙을 따라야합니다.

1. function*를 사용합니다.
function에 *를 사용하게 되면 한 단어를 해제하게 됩니다. 그 단어는 yield입니다.
2. yield
yield는 Generators에서 return처럼 쓰입니다.

```javascript
// Generator function
function* listPeople() {
    yield "Dal";
    yield "Flynn";
    yield "Mark";
    yield "Godkimchi";
    yield "Japan Guy";
}

// Generator function 호출
const listG = listPeople(); // 아무런 일도 일어나지 않습니다.

console.log(listG);
```

console.log(listG)를 보면 {<suspended>} 입니다.
그리고 list.next()를 실행하면..


```javascript
listG.next()
// 출력
// {value: "Dal", done: false}
```

첫번째 value 인 Dal이 출력됨을 확인할 수 있습니다. value만 return하는 것이 아니라 done:false 를 리턴합니다. 이는 generator가 끝나지 않았음을 의미합니다.

계속 .next()를 실행하면..

```javascript
listG.next()
// 출력
// {value: "Dal", done: false}
listG.next()
// 출력
// {value: "Flynn", done: false}
listG.next()
// 출력
// {value: "Mark", done: false}
listG.next()
// 출력
// {value: "Godkimchi", done: false}
listG.next()
// 출력
// {value: "Japan Guy", done: false}

listG.next()
// 출력
// {value: undefined, done: true}
// 이후에 계속 listG.next()를 실행해도 
// 같은 결과 {value: undefined, done: true} 를 출력합니다.
```

#### 사용 예

```javascript
const friends = ["Dal", "Flynn", "Mark", "Godkimchi", "Japan Guy"];

function* friendTeller() {
    for(const friend of friends) {
        yield friend;
    }
}

const friendLooper = friendTeller();
friendLooper.next();
{value: "Dal", done: false}
friendLooper.next();
{value: "Flynn", done: false}
friendLooper.next();
{value: "Mark", done: false}
friendLooper.next();
{value: "Godkimchi", done: false}
friendLooper.next();
{value: "Japan Guy", done: false}
friendLooper.next();
{value: undefined, done: true}
```

yield로 실행을 중지 할 수 있고, next를 호출하여 실행할 수 있습니다.

