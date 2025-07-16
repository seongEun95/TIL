# JavaScript 배열 메서드 정리

## forEach()

- **사용법**:
  ```js
  array.forEach((item, index, arr) => { ... });
  ```

- **반환값**: `undefined`

- **특징**:
  - 배열을 순회하면서 반복 작업 수행
  - 중간에 `break`, `return` 불가능
  - 결과를 저장할 수 없음

---

## map()

- **사용법**:
  ```js
  const newArray = array.map((item, index, arr) => { ... });
  ```

- **반환값**: 새로운 배열

- **특징**:
  - 기존 배열을 변형해 새로운 배열 생성
  - 원본 배열은 변경되지 않음

---

## filter()

- **사용법**:
  ```js
  const filtered = array.filter((item) => item > 10);
  ```

- **반환값**: 조건을 만족하는 요소들로 구성된 새로운 배열

- **특징**:
  - 조건을 만족하는 모든 요소 추출
  - 조건을 만족하는 요소가 없다면 빈 배열 반환

---

## find()

- **사용법**:
  ```js
  const result = array.find((item) => item.id === 3);
  ```

- **반환값**: 조건에 처음 일치하는 요소 (없으면 undefined)

- **특징**:
  - 첫 번째로 조건을 만족하는 요소 하나만 반환
  - filter보다 빠를 수 있음

---

## some()

- **사용법**:
  ```js
  const hasEven = array.some(item => item % 2 === 0);
  ```

- **반환값**: `true` 또는 `false`

- **특징**:
  - 조건을 만족하는 요소가 하나라도 있으면 true
  - 없거나 빈 배열이면 false

---

## every()

- **사용법**:
  ```js
  const allEven = array.every(item => item % 2 === 0);
  ```

- **반환값**: `true` 또는 `false`

- **특징**:
  - 모든 요소가 조건을 만족하면 true
  - 하나라도 만족하지 않으면 false
  - 빈 배열이면 true

---

## reduce()

- **사용법**:
  ```js
  const result = array.reduce((acc, cur) => acc + cur, initialValue);
  ```

- **반환값**: 누적된 결과값

- **특징**:
  - 누산기(acc)와 현재값(cur)을 통해 반복 계산
  - 총합, 평균, 객체 재구성 등 다양한 용도로 활용

---

## sort()

- **사용법**:
  ```js
  array.sort((a, b) => a - b); // 오름차순
  array.sort((a, b) => b - a); // 내림차순
  ```

- **반환값**: 정렬된 원본 배열

- **특징**:
  - 원본 배열이 변경됨
  - 숫자 정렬 시 비교 함수 필요
  - 원본 보존을 원한다면 복사본 생성 후 정렬

---

## reverse()

- **사용법**:
  ```js
  array.reverse();
  ```

- **반환값**: 순서가 반전된 원본 배열

- **특징**:
  - 원본 배열을 직접 뒤집음

---

## new Set()

- **사용법**:
  ```js
  const set = new Set([1, 2, 2, 3]);
  ```

- **반환값**: 중복이 제거된 Set 객체

- **특징**:
  - 중복 제거에 유용
  - 반복 가능
  - 배열로 변환 가능: `[...set]`

---

## new Map 객체

- **사용법**
```js
const userMap = new Map();

userMap.set('id', 123);
userMap.set('name', 'Alice');

console.log(userMap.get('name')); // Alice
console.log(userMap.has('id'));   // true

userMap.delete('id');
console.log(userMap.has('id'));   // false
```

| 메서드               | 반환값                      | 설명                      |
| ----------------- | ------------------------ | ----------------------- |
| `set(key, value)` | **Map 객체 자체**            | 체이닝 가능하게 하기 위해 자기 자신 반환 |
| `get(key)`        | 저장된 **값** 또는 `undefined` | 키에 해당하는 값               |
| `has(key)`        | `true` 또는 `false`        | 해당 키 존재 여부              |
| `delete(key)`     | `true` 또는 `false`        | 삭제 성공 여부 반환             |
| `clear()`         | `undefined`              | 모든 요소 제거, 반환값 없음        |
| `size`            | 숫자                       | 저장된 요소 수                |


- **특징**:
  - 키-값 쌍을 저장할 수 있는 컬렉션 객체
  - 모든 자료형을 키로 사용할 수 있음 (객체, 함수 등도 가능)
  - 삽입된 순서를 유지함 (for...of 등 반복문에 적합)
  - set(), get(), has(), delete(), clear() 등의 메서드 제공
  - 요소 개수는 map.size로 확인
  - 직렬화(JSON.stringify)는 불가능하므로 주의 필요