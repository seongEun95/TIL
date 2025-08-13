# 코요테 3주차

## 1. 어려웠던 부분/문제

대부분이 어려워지기 시작함
근데 정답률이 89퍼센트임..

## 2. 새롭게 알게 된 점

```js
match(); //  메서드
// 주어진 정규 표현식 패턴을 사용하여 문자열 내에서 매치(match, 일치)되는 첫 번째 부분을 찾아내는 함수

const str = 'apple is ...'

const pattern = /apple/;
const result str.match(pattern);
console.log(result) // ['apple'] 을 반환

// 일치하는 부분이 없으면 Null을 리턴
// 일차하는 부분이 발견되면 해당 부분을 포함하는 배열을 반환
```

## 3. 궁금한 점

## 4. 풀면서 느낀 점

쉿,, 생각보다 어렵다
난 아직 애송이구나

일단 문자열 나오면 배열로 만들어버리고 순회해버릴 생각함. Real fact

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

// 숨어있는 숫자의 덧셈 (1) / 변수이름 짓기 귀찮음, reduce 메서드로 합산 결과 냈음.
function solution(my_string) {
  const a = [...my_string];
  const ans = [];
  a.forEach((v) => {
    if (!isNaN(v)) {
      ans.push(Number(v));
    }
  });
  const b = ans.reduce((acc, cur) => {
    return acc + cur;
  });
  return b;
}

// 최댓값 만들기 / 처음에 내림차순 정렬해서 맨 앞에서 요소 2개를 곱하려고 했다가 마이너스 곱도 결국 최대값 되길래 배열의 요소마다 다 곱해버려서 거기서 내림차순 정렬 후 3번째?? 요소를 리턴하니 정답이 됨.
function solution(numbers) {
  const a = numbers;
  const c = [];

  for (let i = 0; i < a.length; i++) {
    for (let j = 0; j < a.length; j++) {
      c.push(a[i] * a[j]);
    }
  }

  const d = c.sort((a, b) => b - a);
  return d[2];
}

// 암호해독 -> [...cipher][code - 1] + [...cipher][code + code - 1] ... 이라는 패턴을 찾아냄 그걸 아래 코드로 표현함.
function solution(cipher, code) {
  var answer = "";
  const a = [...cipher];
  const b = [];

  for (let i = code - 1; i < a.length; i += code) {
    b.push(a[i]);
  }

  return b.join("");
}

// 대문자와 소문자 -> 배열을 순회해서 대문자와 같다면 소문자를 배열에 넣고 아니면 대문자를 배열에 넣어버리면 바꿀 수 있음 Good
function solution(my_string) {
  const arr = [...my_string];
  const ans = [];

  arr.forEach((v) => {
    if (v === v.toUpperCase()) {
      ans.push(v.toLowerCase());
    } else {
      ans.push(v.toUpperCase());
    }
  });
  return ans.join("");
}

// 인덱스 바꾸기 -> splice 메서드로 (시작위치, 삭제갯수, 아이템01...) 사용해서 냄새나게 문제 품.
function solution(my_string, num1, num2) {
  const arr = [...my_string];
  const firstStr = arr.splice(num1, 1);
  const secondStr = arr.splice(num2 - 1, 1);
  const ans01 = arr.splice(num1, 0, secondStr);
  const ans02 = arr.splice(num2, 0, firstStr);

  return arr.join("");
}

// 약수 구하기 -> 나머지 0인 것만 배열에 담아서 반환함, 진짜 빠르게 품.
function solution(n) {
  let ans = [];

  for (let i = 0; i <= n; i++) {
    if (n % i === 0) ans.push(i);
  }
  return ans;
}

// 가장 큰 수 찾기. -> 쉬웠음.
function solution(array) {
  const maxNum = Math.max(...array);
  return [maxNum, array.indexOf(maxNum)];
}

// 문자열 정렬하기 (2) -> sort 사용해서 품
function solution(my_string) {
  const lower = my_string.toLowerCase();
  return [...lower]
    .sort((a, b) => {
      if (a > b) return 1;
      if (a < b) return -1;
    })
    .join("");
}

// 숫자 찾기 -> 나도 메서드 체이닝해서 어렵게 풀어봄
function solution(num, k) {
  const ans = num
    .toString()
    .split("")
    .map((v) => v)
    .indexOf(k.toString());
  return ans === -1 ? -1 : ans + 1;
}
```

## 6. 산뜻한 풀이

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

// 숨어있는 숫자의 덧셈 (1), 정규표현식, replace 써서 숫자만 골라냈다는게 멋지다.
function solution(my_string) {
  const answer = my_string
    .replace(/[^0-9]/g, "")
    .split("")
    .reduce((acc, curr) => acc + Number(curr), 0);
  return answer;
}

// 최댓값 만들기 / j를 i + 1로 해서 자기 자신과 곱하지 않도록 처리했음.
function solution(numbers) {
  var answer = [];
  for (let i = 0; i < numbers.length - 1; i++) {
    for (let j = i + 1; j < numbers.length; j++) {
      answer.push(numbers[i] * numbers[j]);
    }
  }
  return Math.max(...answer);
}

// 암호해독, 메서드 체이닝을 정말 잘하는 거 같음.
function solution(cipher, code) {
  return cipher
    .split("")
    .filter((v, i) => (i + 1) % code === 0)
    .join("");
}

// 대문자와 소문자 -> 메서드 체이닝을 잘하는 거 같음2
function solution(my_string) {
  return my_string
    .split("")
    .map((n) => (n === n.toUpperCase() ? n.toLowerCase() : n.toUpperCase()))
    .join("");
}

// 구조분해 할당응로 산뜻하게 푸심. 천재이신듯.
function solution(my_string, num1, num2) {
  my_string = my_string.split("");
  [my_string[num1], my_string[num2]] = [my_string[num2], my_string[num1]];
  return my_string.join("");
}

// 메서드 체이닝을 기가막히게 잘 쓰시네
function solution(s) {
  return [...s.toLowerCase()].sort().join("");
}

// 숫자 찾기 => 문자열 변환 후에 indexOf 한 게 천재이신듯;
function solution(num, k) {
  return ("❤" + num).indexOf(k);
}
```
