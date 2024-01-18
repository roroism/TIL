# TODAY I LEARNED

## Learned

### History 응용

페이지가 새로고침 되지 않고, 하나의 페이지 안에서 해당 요소로 바로 이동합니다.

```html
<html>
<head>
  <title>Document</title>
  <script type="module" defer src="./main.js"></script>
  <style>
    body {
      margin: 0
    }
    nav {
      background-color: white;
      padding: 10px;
      border: 4px solid;
      position: fixed;
      bottom: 0;
      right: 0;
    }
    nav input {
      width: 50px;
    }
    section {
      height: 100vh;
      border: 10px solid;
      box-sizing: border-box;
    }
    section.page1 { color: red; }
    section.page2 { color: orange; }
    section.page3 { color: green; }
  </style>
</head>
<body>
  <nav>
    <a href="#/page1">p1</a>
    <a href="#/page2">p2</a>
    <a href="#/page3">p3</a>
    <input type="text" />
  </nav>
  <div>
    <section id="/page1" class="page1">
      <h1>Page 1</h1>
    </section>
    <section id="/page2" class="page2">
      <h1>Page 2</h1>
    </section>
    <section id="/page3" class="page3">
      <h1>Page 3</h1>
    </section>
  </div>
</body>
</html>
```
