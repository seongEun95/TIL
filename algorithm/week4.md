# 코요테 4주차

## 1. 어려웠던 부분/문제

- Everything

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

- 단 시간 내에 풀어내야되다 보니 냄새(smell)나는 코드를 작성하게 됨.
- 입문 문제 실화냐 겁나 어렵네

## 5. 문제 풀이 인증 (풀이 완료화면 스크린샷)

```js
// *** 배열만들기 1 -> n이하의 모든 수를 순회하기에 좋지 못한 냄새(smell)나는 코드임.
function solution(n, k) {
  var ans = [];

  for (let i = 1; i <= n; i++) {
    if (i % k === 0) ans.push(i);
  }

  return ans;
}

// *** 접두사 인지 확인하기 -> 단어의 모든 접두사를 배열.slice()를 사용해서 구하고 is_prefix와 비교해서 1을 반환.
// 너무나 많은 배열 순회에 냄새(smell)나는 코드임.
function solution(my_string, is_prefix) {
  const ans = [];
  const a = [...my_string];
  let t = 0;

  a.forEach((v, i, arr) => ans.push(arr.slice(0, i + 1)));

  const d = ans.forEach((v) => (v.join("") === is_prefix ? (t = 1) : null));

  return t;
}

// *** 모스부호 (1) -> 모든 모스부호를 알파벳으로 객체화하여 이를 순회하여 문자열을 만들어버림. -> 의외로 이렇게 푼 사람들이 많아서 냄새(smell)나는 코드인지는 판단불가
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

// *** 2차원으로 만들기 -> for문을 이용하여 배열에 splice메서드로 배열을 잘라 반환 값을 냄. 정답은 맞췄으나 * n이 반복되는 떄려맞추는 신공으로 냄새(smell)나는 코드를 만들어버림.
function solution(num_list, n) {
  let ans = [];

  for (let i = 0; i <= num_list.length * n * n * n; i += n) {
    ans.push(num_list.splice(0, n));
  }
  return ans;
}

// A로 B 만들기 -> 실패함 65퍼 정답인다 나머지 케이스에서 실패함, 찢었다 생각했는데 내가 찢겨버림
function solution(before, after) {
  return [...before].reverse().join("") == after ? 1 : 0;
}

// *** k의 갯수 -> 해당 배열에 k값고 동일한 값이 있는게 아니라 그 숫자가 있는지 판별하는 문제였음. 그래서 배열을 만들고 그 배열을 다 쪼갠다음 비교하여 값을 리턴함.
function solution(i, j, k) {
  const ans = []; // 배열 만들기 위한 빈 배열임
  let num = 0; // 정답임

  // 일단 i ~ j 까지 ans 배열에 밀어 넣음
  for (let a = i; a <= j; a++) {
    ans.push(a);
  }

  // 배열로 만들어진 요소들을 join() 메서드로 한 문자열로 합쳐버림
  // 다시 그걸 배열로 스프레드문법으로 쪼갬
  const arr = [...ans.join("")];

  // 해당 배열을 k와 같은지 비교하여 num을 ++함
  arr.forEach((v) => +v === k && num++);

  // Num 값을 리턴함
  return num;
}

// *** 숨어있는 숫자의 덧셈 (2) -> 문자열에 섞인 숫자만 걸러내기 힘들었음 특히나 34 이런식으로 붙여있는 경우가 있어서 난이도가 높았음.
// 이번 풀이는 얻어걸린거라 막 밀어붙였더니 결국 풀긴 했음. 하지만 누구도 해석하지 못하는 코드가 되어 냄새(smell)나는 코드가 되어버림.
function solution(my_string) {
  // 이건 숫자만 붙여놓기 애매하네;
  const a = [...my_string];
  const b = [];

  // 1. 해당 배열을 순회하여 타입이 숫자인걸 빈배열에 넣음
  a.forEach((v) => {
    if (typeof +v === "number") {
      b.push(+v);
    }
  });

  // 2. 그리고 하나의 문자열로 합친다음 NaN이라고 낫어넘버 문자열을 분리함
  // 3. 그러면 ['', '', 0, 1, '', ''] 요런식으로 나오는데 리듀스로 합계 구하면 됨.
  return b
    .join("")
    .split("NaN")
    .reduce((acc, cur) => acc + +cur, 0);
}

// *** 진료순서 정하기 -> 중복 반복문으로 엄청난 연산을 해버리는 냄새(smell)나는 코드를 양산함.
function solution(emergency) {
  // 내 생각엔 일단 내림차순 정렬을 함
  // emergency [3, 76, 24]
  const c = [...emergency]; // 와 배열을 복사해두었어야 되었네;
  const a = emergency.sort((a, b) => b - a); // [76, 24, 3]
  const b = [];

  // 그리고 인덱스를 구하고
  c.forEach((v, i) => {
    a.forEach((a, j) => {
      if (v === a) {
        b.push(j + 1);
      }
    });
  });
  return b;
}

// 가까운 수 -> "가장 가까운 수가 여러 개일 경우 더 작은 수를 return 합니다." 라는 조건에 무너짐, 제 마음도 무너짐
function solution(array, n) {
  const arr = [...array];
  let c = [];
  // 배열 요소 중 n을 뺐을 때 가장 낮은 숫자를 반환하면 될듯
  const b = arr.map((v, i) => {
    // 마이너스 값
    return Math.abs(v - n);
  });

  console.log(b); // [17, 10, 8]

  const a = Math.min(...b); // 가장 낮은 숫자가 나옴 // 8

  b.forEach((v, i) => {
    if (v === a) {
      c.push(i);
    }
  });

  return array[c[0]];
}

// 7의 갯수 구하기 -> 난이도 정상화, 그냥 하나의 문자열로 합치고 배열로 쪼개고 필터로 7과 같은거 반환 후 길이 값 구함.
function solution(array) {
  return [...array.join("")].filter((v) => +v === 7).length;
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

// k의 갯수 -> 반복문을 한번만 사용해서 푼 문제임
function solution(i, j, k) {
  let a = "";
  for (i; i <= j; i++) {
    a += i;
  }

  return a.split(k).length - 1; // 문자열에 k만큼 잘라서 -1 했구나 / 19191 -> 9로 자르면 '1', '1', '1' 3개 나오므로 -1개
}

// 숨어있는 숫자의 덧셈 (2) -> 정규표현식을 사용하여 숫자만 잘라내어 합을 구하는 레전드 코드를 발견 ㄷ
function solution(my_string) {
  return my_string.split(/\D+/).reduce((acc, cur) => acc + Number(cur), 0);
}

// 진료 순서 정하기 -> slice로 배열 복사, indexOf 메서드로 인덱스를 찾았구나
function solution(emergency) {
  let sorted = emergency.slice().sort((a, b) => b - a);
  return emergency.map((v) => sorted.indexOf(v) + 1);
}

// 7의 갯수 구하기 -> 여기선 split써서 길이를 구함.
function solution(array) {
  return array.join("").split("7").length - 1;
}
```
