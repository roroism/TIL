# TODAY I LEARNED

## Learned

### Array

1. map
		- 매개변수로 넣은 callback함수가 반환하는 값을 모아서 배열과 같은 길이의 새로운 배열을 만둘어줍니다.
		- 얕은복사만 이루어지기때문에 객체배열일때는 원본이 수정되는 것을 주의해야 합니다.
2. find
		- 조건에 맞는 첫번째 item을 반환합니다.
		- item을 반환하면 그 이후의 배열index는 시도하지 않고 종료됩니다.
3. filter
		- 조건에 맞는 item을 모아서 새로운 배열로 반환합니다.
4. sort
		- 내림차순일 경우 sort()뒤에 .reverse()를 사용하거나
		- (a, b) => b - a 콜백함수를 넣어줍니다.

### String

1. trim()
		- 문자열 앞 뒤로 공백을 제거해줍니다.
2. toLowerCase()
		- 영문 문자열을 소문자로 바꿔줍니다.
3. toUpperCase()
		- 영문 문자열을 대문자로 바꿔줍니다.
