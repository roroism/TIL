# TODAY I LEARNED

## Learned

### 웹 접근성 오류 유형 12개 리뷰

#### aria-live

- polite | assertive | off(default)
- 실시간으로 내용을 갱신하는 영역. 예를 들어 ajax를 이용하여 javascript로 동적으로 내용을 갱신할 때 사용.
- 갱신 영역에 polite, assertive값을 사용하면 갱신 순간 보조 기기가 사용자에게 내용을 전달.
- 주로 polite와 assertive 라는 값을 가지고 있다.

```html
<!-- O: 알럿 -->
<div role="alert" aria-live="assertive">
    <p>로그인 후 이용할 수 있습니다.</p>
</div>
<!-- 위 예제는 위에서 말한대로 role="alert" 를 설정하면 자동으로 aria-live="assertive" 가 생기기 때문에 굳이 aria-live="assertive" 를 붙일 필요는 없다. -->
```

##### polite

- polite값은 중요도가 낮은 내용에 사용.
- 현재 진행중인 음성 또는 타이핑을 방해하지 않고 뒤늦게 전달.

### assertive

- assertive값은 중요도가 높은 내용에 사용하여 현재 진행중인 보조기기 작업을중단하고 갱신 내용을 즉시 사용자에게 전달.

