# TODAY I LEARNED

## Learned

### Array.prototype.sort()

`sort()` 메서드는 배열의 요소를 적절한 위치에 정렬한 후 그 배열을 반환합니다. 정렬은 stable sort가 아닐 수 있습니다. 기본 정렬 순서는 문자열의 유니코드 코드 포인트를 따릅니다.

#### 내림차순 정렬

```
nums.sort((a, b) => b - a);
```

#### 한 자리수 숫자를 오름차순 정렬

```
nums.sort();
```

#### 두 자릿수 이상의 숫자를 오름차순 정렬

```
nums.sort((a, b)=>a-b);
```
