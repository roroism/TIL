# TODAY I LEARNED

## 복습

### DOM 요소 수정하기

#### 요소의 텍스트 변경하기

- 텍스트 값을 수정하려면 textContent 속성을 설정합니다.

```javascript
<body>
  <h1 id="bigMessage" class="highlight summer">What's happening?</h1>

  <script>
    let headingElement = document.querySelector("#bigMessage");
    headingElement.textContent = "Oppa Gangnam Style!";
  </script>
</body>
```

#### 요소의 속성 값 변경하기

- setAttribute를 사용합니다.

**setAttribute**

```javascript
<body>
  <button>Hello World</button>

  <script>
    const button = document.querySelector("button");
    button.setAttribute("name", "helloButton");
    button.setAttribute("disabled", "");
  </script>
</body>
```

##### id와 class 속성의 수정

- id와 class 두 속성은 다른 방법으로 설정해야 합니다.
- html 요소는 id 및 classNameproperties를 직접 노출합니다.
- 요소.id 으로 id값을 조회하고 설정할 수 있습니다.
- 요소.className 으로 class값을 조회하고 설정할 수 있습니다.
- 이외에도 다른 방법이 더 존재합니다.

```javascript
<body>
  <div id="exampleDiv" class="exampleClass">Hello, World!</div>

  <script>
    // id와 class를 확인하고 설정하는 함수
function manipulateElement() {
    // id가 "exampleDiv"인 요소를 가져옴
    var elementById = document.getElementById("exampleDiv");
    // class가 "exampleClass"인 요소를 모두 가져옴
    var elementsByClass = document.getElementsByClassName("exampleClass");

    // id가 "exampleDiv"인 요소의 id를 출력
    console.log("Element's ID:", elementById.id);

    // class가 "exampleClass"인 요소들의 class를 출력
    console.log("Elements' Classes:");
    for (var i = 0; i < elementsByClass.length; i++) {
        console.log(elementsByClass[i].className);
    }

    // id를 변경하고 class를 추가
    elementById.id = "newExampleDiv";
    elementById.className += " newClass";
}

// 함수 호출
manipulateElement();
  </script>
</body>
```

- 여기서 주의할 점은 class 속성을 사용하기 위해 class라는 문구를 사용할 수 없습니다.
- 그 이유는 JavaScript에서 class라는 이름을 다른 용도로 사용하기 때문입니다.
- 그래서 class 객체 처리와 관련해서는 className 이라는 명칭을 대신 사용해야 합니다.

#### 참고

- https://cpro95.tistory.com/144

