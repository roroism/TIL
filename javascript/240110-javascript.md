# TODAY I LEARNED

## Learned

### 커스텀 이벤트와 디스패치

**디스패치**

- 화면에서 실제로 이벤트를 발생시키지 않아도 dispatchEvent 메소드를 사용하여 강제로 이벤트를 발생시킬 수 있습니다.
    - 인수로는 이벤트 인스턴스를 넘겨줍니다. 예 : `new Event('click')`

**커스텀 이벤트**

- javascript에는 존재하지 않는 이벤트라도 dispatchEvent 메소드를 사용하면 이벤트를 강제로 발생시킬 수 있습니다.

#### 예시 코드

##### 디스패치 예시

```javascript
// 디스패치

const child1 = document.querySelector('.child:nth-child(1)');
const child2 = document.querySelector('.child:nth-child(2)');

child1.addEventListener('click', event => {
  // 강제로 이벤트 발생!
  child2.dispatchEvent(new Event('click'));
  child2.dispatchEvent(new Event('wheel'));
  child2.dispatchEvent(new Event('keydown'));
});
child2.addEventListener('click', event => {
  console.log('Child2 Click!');
});
child2.addEventListener('wheel', event => {
  console.log('Child2 Wheel!');
});
child2.addEventListener('keydown', event => {
  console.log('Child2 Keydown!');
});
```

##### 커스텀 이벤트 예시

```javascript
// 커스텀 이벤트

const child1 = document.querySelector('.child:nth-child(1)');
const child2 = document.querySelector('.child:nth-child(2)');

// addEventListener에 javascript에는 존재하지 않는 'hello-world' 라는 커스텀 이벤트를 연결했습니다.
// 당연하게도 hello-world 이벤트는 어떠한 경우에도 발생하지 않습니다.
child1.addEventListener('hello-world', event => {
  console.log('커스텀 이벤트 발생!');
  console.log(event.detail);
});

// 하지만, dispatchEvent를 이용하여 이벤트를 강제로 발생시키면
// 임의의 이름으로 만든 이벤트를 동작시킬 수 있습니다.
child2.addEventListener('click', () => {
  child1.dispatchEvent(new Event('hello-world'));
});
```

##### 커스텀 이벤트 예시2

Event 생성자 함수 뿐만 아니라 CustomEvent 생성자 함수라는 것도 존재합니다.

```javascript
// 커스텀 이벤트

const child1 = document.querySelector('.child:nth-child(1)');
const child2 = document.querySelector('.child:nth-child(2)');

child1.addEventListener('hello-world', event => {
  console.log('커스텀 이벤트 발생!');
  console.log(event.detail);
});

// Event 대신 CustomEvent 생성자 함수를 사용하고, 두번째 인수로 객체를 넘겨줍니다.
// 
child2.addEventListener('click', () => {
  child1.dispatchEvent(new CustomEvent('hello-world'), {detail: 123});
});
```

javascript에 존재하지 않는 custom한 이벤트를 만들 수도 있고 실행할 수도 있는데, 만약 실행 할 때 어떤 데이터를 같이 전달하고 싶으면 두번째 인수로 detail 속성에 데이터를 추가하고 객체로 넘겨주면 됩니다.

detail 속성을 이용하여 데이터를 넘겨주고 싶다면 Event 생성자 함수가 아닌 CustomEvent 생성자 함수를 사용해야 합니다.

