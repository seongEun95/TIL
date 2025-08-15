# 코요테 4주차

## 1. 어려웠던 부분/문제

## 2. 새롭게 알게 된 점

```js
array.flat(n);
// 중첩 배열을 n만큼 평탄화 함.

const result = arr1.flatMap((num) => (num === 2 ? [2, 2] : 1)); // 반환값 : [1, 2, 2, 1]
// flatMap -> arr.map(...args).flat() 과 동일한 과정임.

str.split(" ");
// 구분자로 문자열을 분리하여 배열로 만듬.
```

## 3. 궁금한 점

## 4. 풀면서 느낀 점

## 5. 문제 풀이 인증 (풀이 완료화면 스크린샷)

```js
// 배열만들기 1 -> n이하의 모든 수를 순회하기에 좋지 못한 냄새(smell)나는 코드임.
function solution(n, k) {
  var ans = [];

  for (let i = 1; i <= n; i++) {
    if (i % k === 0) ans.push(i);
  }

  return ans;
}

// 접두사 인지 확인하기 -> 단어의 모든 접두사를 배열.slice()를 사용해서 구하고 is_prefix와 비교해서 1을 반환.
// 너무나 많은 배열 순회에 냄새(smell)나는 코드임.
function solution(my_string, is_prefix) {
  const ans = [];
  const a = [...my_string];
  let t = 0;

  a.forEach((v, i, arr) => ans.push(arr.slice(0, i + 1)));

  const d = ans.forEach((v) => (v.join("") === is_prefix ? (t = 1) : null));

  return t;
}

// 모스부호 (1) -> 모든 모스부호를 알파벳으로 객체화하여 이를 순회하여 문자열을 만들어버림. -> 의외로 이렇게 푼 사람들이 많아서 냄새(smell)나는 코드인지는 판단불가
function solution(letter) {
  const al = {
    ".-": "a",
    "-...": "b",
    "-.-.": "c",
    "-..": "d",
    ".": "e",
    "..-.": "f",
    "--.": "g",
    "....": "h",
    "..": "i",
    ".---": "j",
    "-.-": "k",
    ".-..": "l",
    "--": "m",
    "-.": "n",
    "---": "o",
    ".--.": "p",
    "--.-": "q",
    ".-.": "r",
    "...": "s",
    "-": "t",
    "..-": "u",
    "...-": "v",
    ".--": "w",
    "-..-": "x",
    "-.--": "y",
    "--..": "z",
  };

  const arr = letter.split(" ");
  let ans = "";
  arr.forEach((v, i) => {
    ans = ans + al[v];
  });
  return ans;
}

// 2차원으로 만들기 -> for문을 이용하여 배열에 splice메서드로 배열을 잘라 반환 값을 냄. 정답은 맞췄으나 * n이 반복되는 떄려맞추는 신공으로 냄새(smell)나는 코드를 만들어버림.
function solution(num_list, n) {
  let ans = [];

  for (let i = 0; i <= num_list.length * n * n * n; i += n) {
    ans.push(num_list.splice(0, n));
  }
  return ans;
}
```

## 6. 산뜻한 풀이

```js
// 배열만들기 1 -> for 반복문에서 i = k, i = i + k로 진행해서 딱 배수만 반환되도록 설계함.
function solution(n, k) {
  var answer = [];
  for (let i = k; i <= n; i += k) {
    answer.push(i);
  }
  return answer;
}

// 접두사 인지 확인하기 -> 그냥 문자열에 slice하여 푼 문제
function solution(my_string, is_prefix) {
  return my_string.slice(0, is_prefix.length) === is_prefix ? 1 : 0;
}

// 2차원으로 만들기 -> while문을 사용했고 splice메서드로 배열이 어차피 짤리니깐 결국 0이되서 멈추게 되어있음. 그걸 배열로 push해서 반환했구나
function solution(num_list, n) {
  var answer = [];

  while (num_list.length) {
    answer.push(num_list.splice(0, n));
  }

  return answer;
}
```
