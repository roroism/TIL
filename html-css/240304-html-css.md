# TODAY I LEARNED

## 복습

### 시각적으로 숨기고 접근성 유지하기

- 아래 css를 코드를 숨기고 싶은 엘리먼트의 class에 적용하면 됨.

**naver 페이지에서 사용하고 있는 css코드**

```css
.blind {
    position: absolute;
    clip: rect(0 0 0 0);
    width: 1px;
    height: 1px;
    margin: -1px;
    overflow: hidden;
}
```

```css
.sr-only {
    position: absolute !important;
    width: 1px !important;
    height: 1px !important;
    padding: 0 !important;
    overflow: hidden !important;
    clip: rect(0, 0, 0, 0) !important;
    white-space: nowrap !important;
    border: 0 !important;
}
```

