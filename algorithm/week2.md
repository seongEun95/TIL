# 코요테 2주차


## 1. 어려웠던 부분/문제


## 2. 새롭게 알게 된 점
- slice 배열 메서드 (자르고 배열 복사)
  - 배열의 일부분을 잘라 "새로운 배열"로 반환
  - 원본 배열은 변경되지 않음
```js
array.slice(start, end);
```
  - start: 시작 인덱스 (포함)
  - end: 끝 인덱스 (미포함)
  - 둘 다 생략시 전체 배열 복사

- splice 배열 메서드 (자르고 원본 수정)
  - 배열의 특정 구간을 잘라내거나 잘라내고 새로운 요소 삽입가능까지 가능
  - 원본 배열을 변경
```js
array.splice(start, deleteCount, item1, item2, ...);
```  
 - start: 수정 시작 인덱스
 - deleteCount: 제거할 요소 개수
 - item: start 위치에 새로 넣을 요소(옵션) 

## 3. 궁금한 점


## 4. 풀면서 느낀 점
- slice, splice 이름도 비슷해가지고 헷갈렸음. 이참에 정리하고 좋았음.


## 5. 문제 풀이 인증 (풀이 완료화면 스크린샷)
```js
function solution(numbers, num1, num2) {
    var answer = numbers.slice(num1, num2 + 1)
    return answer;
}
```

## 6. 이번 풀이 소감

```js

```