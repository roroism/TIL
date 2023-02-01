# TODAY I LEARNED

## Learned

### HTML Fragments

사용 예

```javascript
const wrapper = documents.querySelector(".wrapper");

const addWelcome = () => {
  const div = `
    <div class="hello">
      <h1 class="title">Hello</h1>
    </div>
  `;
  wrapper.innerHTML = div;
};

setTimeout(addWelcome, 2000);
```

사용 예2

```javascript
const wrapper = document.querySelector(".wrapper");

const friends = ["me", "lynn", "dal", "mark"];

const list = `
  <h1>People i love</h1>
  <ul>
    ${friends.map(friend => `<li>${friend}</li>`).join("")}
  </ul>
`;

wrapper.innerHTML = list;
```

