# TODAY I LEARNED

## Learned

### ECMAScript 2023 살펴보기

- ECMAScript 2023 명세서 : `https://tc39.es/ecma262/2023/#sec-numbers-and-dates`

### Finished Proposals

2023의 Finished Proposals 들.

- Array find from last
- Hashbang Grammar
- Symbols as WeakMap keys
- Change Array by Copy

### Array Method

6개의 배열 관련 메서드가 새롭게 추가됩니다.
- findLast
- findLastIndex
- toSorted
- toReversed
- toSpliced
- with

#### Array find from last (마지막부터 배열 찾기)

- findLast()
- findLastIndex()
- 기존 배열의 find(), findIndex() 메서드는 배열의 첫 번째 원소부터 찾기 시작합니다.
- 이번에 추가된 findLast(), findLastIndex() 메서드는 반대로 배열의 맨 뒤 원소부터 찾기 시작합니다.

##### 새로 추가된 이유

- 배열에서 일부 인덱스를 찾는 기능으로 {Array, %TypedArray%}.prototype.indexOf 와 {Array, %TypedArray%}.prototype.lastIndexOf 를 지원합니다. (인덱스 찾기o, 요소 찾기x, 조건 함수x, 뒤부터 찾기o)
- 조건 함수를 사용하여 배열에서 요소나 해당 인덱스를 찾는 방법으로 {Array, %TypedArray%}.prototype.find 와
{Array, %TypedArray%}.prototype.findIndex 를 지원합니다. (인덱스 찾기o, 요소 찾기o, 조건 함수o, 뒤부터 찾기x)
- 하지만, 조건 함수를 사용하여 배열의 마지막부터 첫 번째까지 요소를 찾는 방법을 제공하지 않았습니다.
- 기존에 있는 함수로 해결하는 방법으로는 .reverse().find() .reverse().findIndex() 가 있지만 3가지 문제가 있습니다.
- 1. 불필요한 돌연변이(역방향(.reverse)) 2. 불필요한 복사본(원본 변이를 피하기 위해) 3. 복잡한 지수 계산(findIndex에서 index다시 계산)

##### findLast와 findLastIndex가 유용한 경우

- 마지막에서부터 찾는 것이 더 나은 성능을 가질 수 있습니다. 예 : 타임라인에서 최근에 일치하는 시점을 찾을 때.
- 요소의 순서가 중요한 경우. 예 : 숫자 목록의 마지막 홀수를 찾을 때.

##### findLast와 findLastIndex 예시코드

```javascript
const isEven = (number) => number % 2 === 0;
const numbers = [1, 2, 3, 4];

// 첫 번째 원소에서 마지막 순서로 찾기 실행
console.log(numbers.find(isEven));
// 2
console.log(numbers.findIndex(isEven));
// 1

// 마지막 원소에서 첫 번째 원소로 역순으로 찾기 실행
console.log(numbers.findLast(isEven));
// 4
console.log(numbers.findLastIndex(isEven));
// 3
```

#### Change Array by Copy (복사하여 배열 변경)

- Array.prototype.toReversed() -> Array
- Array.prototype.toSorted(compareFn) -> Array
- Array.prototype.toSpliced(start, deleteCount, ...items) -> Array
- Array.prototype.with(index, value) -> Array
- 대상 배열을 그대로 유지하고, 대신 변경 사항이 수행된 복사본을 반환합니다.

##### 새로 추가된 이유

- 기존 reverse(), sort(), splice() 메서드는 해당 배열에 직접 수정을 가합니다.
- 기존 함수들의 동작방식은 함수의 실행 결과가 원본에 영향을 미치지 않는 순수 함수여야 한다는 함수형 패러다임에 부합하지 않습니다.
- 그래서 기존 함수로는 함수의 원본을 해치지 않기 위해서는 전체적인 배열 요소를 한 번 복사하는 과정이 필수적입니다.
- 새로 추가된 함수들은 원본에 수정을 가하지 않고, 결과값을 새로운 배열로 담아 리턴합니다.

##### toSorted()

새로운 toSorted()

```javascript
// toSorted() 사용
// 원본에 영향을 미치지 않고, 결과값을 새로운 배열로 반환
const sortTarget = [1, 2, 3, 4, 5];
const sorted = sortTarget.toSorted((a, b) => b - a); // 내림차순으로 배열 요소를 정렬 

console.log(sortTarget); // [1, 2, 3, 4, 5];
console.log(sorted); // [5, 4, 3, 2, 1];
```

##### toReversed()

새로운 toReversed()

```javascript
const reverseTarget = [1, 2, 3, 4, 5];
const reversed = reverseTarget.reverse();

console.log(reverseTarget); // [5, 4, 3, 2, 1]
console.log(reversed); // [5, 4, 3, 2, 1]
```

##### toSpliced()

- 기존의 splice()는 splice(제거를 시작할 인덱스, 제거 개수, 새롭게 넣을 요소) 로 사용하며, 원본 배열은 수정되고 배열에서 제거된 부분이 메서드 결과로 반환됩니다.
- toSpliced() 는 원본 배열을 수정하지 않고 제거된 부분으로 새로운 배열을 만듭니다.
- 반대로 기존의splice()처럼 toSpliced()를 사용하여 새롭게 요소를 넣은 배열을 반환받을 수 있습니다.
- 기존 splice()

새로운 toSpliced()

```javascript
const spliceTarget = [1, 2, 3, 4, 5];
const spliced = spliceTarget.toSpliced(0, 2, ...[6, 7]);

console.log(spliceTarget); // [1, 2, 3, 4, 5]
console.log(spliced); // [6, 7, 3, 4, 5]
```

##### with()

- with() 메서드는 두 개의 인자를 가집니다. (위치, 첫 번째 인자의 위치의 값을 두 번째 인자값으로 변경하는 값)
- 원본에 영향을 주지 않고, 결과값을 새로운 배열로 리턴합니다.
- Array 인스턴스의 with() 메서드는 주어진 인덱스의 값을 변경하기 위해 대괄호 표기법을 사용하는 것의 복사 버전입니다.

```javascript
// 하나의 요소만 변경한채로 새로운 배열을 만들기
const arr = [1, 2, 3, 4, 5];
console.log(arr.with(2, 6)); // [1, 2, 6, 4, 5]
console.log(arr); // [1, 2, 3, 4, 5]

// 배열 메서드 연속하여 연결하기
const arr = [1, 2, 3, 4, 5];
console.log(arr.with(2, 6).map((x) => x ** 2)); // [1, 4, 36, 16, 25]
```

### 정리

ECMAScript 2023에서는 기존에 있던 메서드를 순수 함수 버전으로 제공하거나 편의성을 위한 메서드들이 새롭게 추가되었습니다. 새롭게 추가된 함수들은 map, filter, reduce와 같은 메서드들과 조합하여 유용하게 사용할 수 있습니다.

출처 : `https://iyu88.github.io//javascript/2023/04/23/ecma-script-2023.html`
출처 : `https://mycodings.fly.dev/blog/2023-05-22-ecmascript-2023-4-new-features`
출처 : `https://github.com/tc39/proposal-array-find-from-last`

