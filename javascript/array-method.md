## forEach() 함수 
- 배열을 순회, 각 요소를 콜백 함수로 처리하기 위한 함수

```javascript
const arr = ["사과", "포도", "복숭아"];

arr.forEach((el) => {
  console.log(el) 
})

// "사과"
// "포도"
// "복숭아"
```

## map() 함수
- 배열을 순회해서 처리한 새로운 배열을 반환하는 함수
- 원본 배열은 변경하지 않는다.

```javascript
const num = [1, 2, 3, 4, 5];

const doubleNum = num.map((num) => {
  return num * 2;
})

// 반환값 : [2, 4, 6, 8, 10]
```