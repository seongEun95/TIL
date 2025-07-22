# Promise

Promise는 비동기 작업이 완료되면 값을 알려 주는 객체입니다.

### 3가지 상태
- Pending: 비동기 작업이 끝나기를 기다릴 때
- Fulfilled: 비동기 작업이 성공적으로 끝났을 때. 비동기 작업의 성공 결과를 결괏값으로 갖게 됨.
- Rejected: 비동기 작업이 실패했을 때. 비동기 작업에서 발생한 오류를 결괏값으로 갖게 됨.

```js

// async, await 문법
// await는 Promise가 fulfilled될 때까지 기다렸다가, 그 결과값을 반환한다.
// await는 반드시 async 함수 내부에서만 사용할 수 있다.
// await 없이 fetch()를 쓰면 Promise 객체 자체가 반환된다 (Pending 상태)
const userData = {
  name: '',
  age: 25,
}

async function asyncFunc() {
  try {
    const response = await fetch('https://abc.kr/api/get', {
      method: 'POST',
      body: JSON.stringify(userData),
      headers: {
        'Content-Type': 'application/json'
      }
    })
    const data = await response.json() // json 데이터로 파싱
    console.log(data)
  } catch (error) {
    console.error('Error fetching data:', error)
  } finally {
    console.log('무조건 실행');
  }
}


// then method
// then: 성공시 실행할 콜백
// catch: 실패시 실행할 콜백
// finally: 성공, 실패와 무관하게 무조건 실행
fetch('https://abc.kr/api/get', {
  method: 'POST',
  body: JSON.stringify(userData),
  headers: {
    'Content-Type': 'application/json'
  }
})
.then((response) => {
  if (!response.ok) { // fetch는 네트워크 에러가 아닌 이상 catch로 가지 않기 때문에 상태 체크 필요
    throw new Error(`Network response was not ok: ${response.statusText}`);
  }
  return response.json();
})
.then((data) => console.log(data))
.catch((error) => console.error('Error fetching data:', error))
.finally(() => console.log('무조건 실행'));

// axios 사용 예제
// axios는 내부적으로 status 코드에 따라 자동으로 reject 처리해주기 때문에 response.ok 확인이 불필요
// 자동으로 JSON 변환까지 한다.
import axios from 'axios';

async function fetchDataWithAxios() {
  try {
    const response = await axios.post('https://abc.kr/api/get', userData, {
      headers: {
        'Content-Type': 'application/json'
      }
    });
    console.log(response.data); // 응답 데이터를 출력합니다.
  } catch (error) {
    console.error('Error fetching data with axios:', error);
  } finally {
    console.log('무조건 실행');
  }
}

fetchDataWithAxios();

// Promise.add()
// Promise.all()`은 여러 개의 Promise를 병렬로 실행하고 모든 Promise가 성공했을 때만 전체 결과를 반환
// 하나라도 실패하면 전체가 실패(rejected) 처리
Promise.all([promise1, promise2, ...])
  .then((results) => {
    // 모든 Promise가 fulfilled되었을 때 실행
  })
  .catch((error) => {
    // 하나라도 rejected되었을 때 실행
  });

```
