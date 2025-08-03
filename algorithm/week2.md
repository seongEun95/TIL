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
- slice, splice 이름도 비슷해가지고 헷갈렸음. 
- 이참에 정리하고 좋았음.


## 5. 문제 풀이 인증 (풀이 완료화면 스크린샷)
```js
// 삼각형의 완성조건 (1)
function solution(sides) {
    const sortedSides = sides.sort((a,b) => b - a);
    return sortedSides[0] < sortedSides[1] + sortedSides[2] ? 1 : 2;
}

// 배열 자르기
function solution(numbers, num1, num2) {
    var answer = numbers.slice(num1, num2 + 1)
    return answer;
}

// 피자 나눠먹기 (3)
function solution(slice, n) {
    return Math.ceil(n / slice)
}

// 점의 위치 구하기 (정직하게 풀어버림)
function solution(dot) {
    // [양수, 양수] : 1
    // [양수, 음수] : 4
    // [음수, 양수] : 2
    // [음수, 음수] : 3
    
    if(dot[0] > 0 && dot[1] > 0) return 1;
    if(dot[0] > 0 && dot[1] < 0) return 4;
    if(dot[0] < 0 && dot[1] > 0) return 2;
    if(dot[0] < 0 && dot[1] < 0) return 3;
}

// 점의 위치 구하기 다른사람풀이 (구조분해할당 방식)
function solution(dot) {
    const [num, num2] = dot;
    const check = num * num2 > 0;
    return num > 0 ? (check ? 1 : 4) : (check ? 3 : 2);
}

// 배열의 유사도 (콜백헬 느낌으로 풀음 (이중 반복문))
function solution(s1, s2) {

  let ans = 0;

  s1.forEach((v1) => {
    s2.forEach((v2) => {
      if( v1 === v2){
          ans++
      }
    })
  })

  return ans;
}


// 순서쌍의 개수 (모든 수를 대입하는 비효율 끝판왕 방법, 더 좋은 방법 모르겠음)
function solution(n) {
    let count = 0;
   for(let i = 0; i <= n; i++){
       if(n % i === 0){
           count++
       }
   }
    return count;
}

// 배열 원소의 길이 (각 배열의 길이를 push해서 반환)
function solution(strlist) {
    const ans = [];
    strlist.forEach((v) => {ans.push(v.length)})   
    return ans;
}
```

## 6. 이번 풀이 소감

```js

```