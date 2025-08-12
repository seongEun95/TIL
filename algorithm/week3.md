# 코요테 3주차

## 1. 어려웠던 부분/문제

## 2. 새롭게 알게 된 점

## 3. 궁금한 점

## 4. 풀면서 느낀 점

쉿,, 생각보다 어렵다

## 5. 문제 풀이 인증 (풀이 완료화면 스크린샷)

```js
// 개미군단
function solution(hp) {
  const j = 5;
  const b = 3;
  const w = 1;

  let result = 0;

  result += Math.floor(hp / j); // 장군 개미
  hp %= j; // 나머지 대입

  result += Math.floor(hp / b); // 병정 개미
  hp %= b; // 나머지 대입

  result += Math.floor(hp / w); // 일 개미

  return result;
}

// 가위 바위 보, 객체 이용해서 품
function solution(rsp) {
  // r = 2 가위
  // s = 0 바위
  // p = 5 보

  const obj = {
    2: "0",
    0: "5",
    5: "2",
  };

  const arr = [...rsp];

  const a = arr.map((v) => {
    return obj[v];
  });

  return a.join("");
}

// 주사위 개수, 이게 알고리즘인가?
function solution(box, n) {
  // box : 가로, 세로 높이가 저장되어 있는 배열
  // n : 주사위 모서리의 길이 정수

  var a = parseInt(box[0] / n);
  var b = parseInt(box[1] / n);
  var c = parseInt(box[2] / n);

  return a * b * c;
}

// 문자열 정렬하기, isNaN을 잘 이용한듯
function solution(my_string) {
  const arr = [];
  const sarr = [...my_string];

  sarr.forEach((v) => {
    if (!isNaN(v)) {
      arr.push(+v);
    }
  });
  return arr.sort((a, b) => a - b);
}
```

## 6. 참신한 풀이

```js
// 주사위 개수, 배열 디스트럭처링이 직관적으로 잘 이용하신 듯
function solution(box, n) {
  let [width, length, height] = box;
  return Math.floor(width / n) * Math.floor(length / n) * Math.floor(height / n);
}

// 문자열 정렬하기, match 메서드, 정규표현식을 잘 이용하신 듯.
function solution(my_string) {
  return my_string
    .match(/\d/g)
    .sort((a, b) => a - b)
    .map((n) => Number(n));
}
```
