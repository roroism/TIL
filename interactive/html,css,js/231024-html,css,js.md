# TODAY I LEARNED

## Learned

### 헤더 영역 실습 - 1

#### 알게된 내용

- flex 안의 item의 가로 값을 고정으로 결정하고 싶을 때, width 대신 flex-width 을 사용할 수도 있다. 참고로 width 보다 flex-width가 우선순위가 높다.

```css
#magnifying-glass-wrapper {
  flex-basis: 32px;
  flex-shrink: 0;
  height: 32px;
}
```

