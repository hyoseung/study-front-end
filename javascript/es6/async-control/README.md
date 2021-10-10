# 비동기 제어

## Callback

콜백함수를 이용하면 특정 로직이 끝났을 때 원하는 동작을 실행시킬 수 있음

```javascript
// ajax

function getData(callbackFunc) {
    $.get('https://domain.com/products/1', function(res) {
        callbackFunc(res); // 서버에서 받은 데이터 res를 callbackFunc() 함수에 넘겨줌
    });
}

getData(function(result) {
    console.log(result); // $.get()의 res값이 result에 전달됨
});
```

### Callback hell (콜백지옥)

* 콜백 함수를 익명 함수로 전달하는 과정이 반복되어 코드의 들여쓰기 수준이 감당하기 힘들정도로 깊어지는 현상
* 주로 이벤트 처리나 서버 통신과 같은 비동기적인 작업을 수행하기 위해 이런 형태가 자주 등장하는데, 가독성이 떨어지면서 코드를 수정하기 어렵움

```javascript
setTimeout(
  (name) => {
    let coffeeList = name;
    console.log(coffeeList);

    setTimeout(
      (name) => {
        coffeeList += ', ' + name;
        console.log(coffeeList);

        setTimeout(
          (name) => {
            coffeeList += ', ' + name;
            console.log(coffeeList);

            setTimeout(
              (name) => {
                coffeeList += ', ' + name;
                console.log(coffeeList);
              },
              500, 'Latte',
            );
          },
          500, 'Mocha',
        );
      },
      500, 'Americano',
    );
  },
  500, 'Espresso',
);

// Espresso
// Espresso, Americano
// Espresso, Americano, Mocha
// Espresso, Americano, Mocha, Latte
```

#### 해결 방법

* 기명함수
* `Promise` -> ES6
* `async & await` -> ES8

기명함수 예시

```javascript
let coffeeList = '';

const addEspresso = (name) => {
  coffeeList = name;
  console.log(coffeeList);
  setTimeout(addAmericano, 500, 'Americano');
};

const addAmericano = (name) => {
  coffeeList += ', ' + name;
  console.log(coffeeList);
  setTimeout(addMocha, 500, 'Mocha');
};

const addMocha = (name) => {
  coffeeList += ', ' + name;
  console.log(coffeeList);
  setTimeout(addLatte, 500, 'Latte');
};

const addLatte = (name) => {
  coffeeList += ', ' + name;
  console.log(coffeeList);
};

setTimeout(addEspresso, 500, 'Espresso');
```

## Promise

* `Promise`는 자바스크립트 비동기 처리에 사용되는 객체

```javascript
function getData(callback) {
  // new Promise() 추가
  return new Promise(function(resolve, reject) {
    $.get('url 주소/products/1', function(res) {
      // 데이터를 받으면 resolve() 호출
      resolve(res);
    });
  });
}

// getData()의 실행이 끝나면 호출되는 then()
getData().then(function(result) {
  // resolve()의 결과 값이 여기로 전달됨
  console.log(result); // $.get()의 res 값이 result에 전달됨
});
```

### Promise의 3가지 상태

* 3가지 상태란 Promise의 처리과정을 의미
* `new Promise()` 로 Promise를 생성하고 종료될 때까지 3가지 상태를 갖는다

#### Pending (대기)

* 비동기 처리 로직이 아직 완료되지 않은 상태
* `new Promise()` 메서드를 호출하면 `대기(Pending)` 상태가 됨
* `new Promise()` 메서드를 호출할 때 콜백 함수를 선언할 수 있음
* 콜백함수 인자는 `resolve`, `reject`

```javascript
new Promise(function(resolve, reject) {
  // ...
});
```

#### Fulfilled (이행)

* 비동기 처리가 완료되어 Promise 결과 값을 반환해준 상태
* 콜백함수의 인자 `resolve`를 호출하면 `이행(Fulfilled)` 상태가 됨
* 이행상태가 되면 `then()`을 이용해서 처리 결과 값을 받을 수 있음

```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// resolve()의 결과 값 data를 resolvedData로 받음
getData().then(function(resolvedData) {
  console.log(resolvedData); // 100
});
```

#### Rejected (실패)

* 비동기 처리가 실패하거나 오류가 발생한 상태
* 콜백함수의 인자 `reject`를 호출하면 `실패(Rejected)` 상태가 됨
* 실패상태가 되면 `catch()`로 받을 수 있음

```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// reject()의 결과 값 Error를 err에 받음
getData().then().catch(function(err) {
  console.log(err); // Error: Request is failed
});
```

![](<../../../.gitbook/assets/image (17).png>)

### Promise 사용 예

```javascript
function getData() {
  return new Promise({
    // ...
  });
}

// then() 으로 여러 개의 프로미스를 연결한 형식
getData()
  .then(function(data) {
    // ...
  })
  .then(function() {
    // ...
  })
  .then(function() {
    // ...
  });
```

```javascript
new Promise(function(resolve, reject){
  setTimeout(function() {
    resolve(1);
  }, 2000);
})
.then(function(result) {
  console.log(result); // 1
  return result + 10;
})
.then(function(result) {
  console.log(result); // 11
  return result + 20;
})
.then(function(result) {
  console.log(result); // 31
});
```

### Promise 에러 처리

#### `catch()`를 이용하는 방법 (이 방법 사용하기!)

```javascript
getData().then().catch();

// 
function getData() {
  return new Promise(function(resolve, reject) {
    reject('failed');
  });
}

getData().then().catch(function(err) {
  console.log(err);
});
```

#### `then()`의 두번째 인자로 에러를 처리하는 방법

```javascript
getData().then(
  handleSuccess,
  handleError
);

// 예
function getData() {
  return new Promise(function(resolve, reject) {
    reject('failed');
  });
}

getData().then(function() {
  // ...
}, function(err) {
  console.log(err);
});
```

## async & await

* ES8
* 기존의 비동기 처리 방식인 콜백함수와 Promise의 단점을 보완

```javascript
// 기존코드
function logName() {
  // fetchUser() 메서드가 서버에서 사용자 정보를 가져오는 HTTP 통신 코드라고 가정
  var user = fetchUser('domain.com/users/1', function(user) {
    if (user.id === 1) {
      console.log(user.name);
    }
  });
}
```

```javascript
// async, await 적
async function logName() {
  var user = await fetchUser('domain.com/users/1');
  if (user.id === 1) {
    console.log(user.name);
  }
}
```

### async & await 사용 예

```javascript
function fetchItems() {
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      var items = [1,2,3];
      resolve(items)
    }, 3000);
  });
}

async function logItems() {
  var resultItems = await fetchItems();
  console.log(resultItems); // [1,2,3]
}
```

### async & await 에러 처리

`Promise`에서 에러 처리를 위해 `.catch()`를 사용했던 것처럼 `async`에서는 `catch {}` 사용

```javascript
async function logTodoTitle() {
  try {
    var user = await fetchUser();
    if (user.id === 1) {
      console.log(todo.title);
    }
  } catch (error) {
    console.log(error);
  }
}
```

## 참고

* [captain pangyo | 자바스크립트 비동기 처리와 콜백 함수](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)
* [captain pangyo | 자바스크립트 Promise 쉽게 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
* [captain pangyo | 자바스크립트 async와 await](https://joshua1988.github.io/web-development/javascript/js-async-await/)
* [yujo | 2020년 8월 31일 | \[JS\]콜백 지옥 탈출하기](https://velog.io/@yujo/JS%EC%BD%9C%EB%B0%B1-%EC%A7%80%EC%98%A5%EA%B3%BC-%EB%B9%84%EB%8F%99%EA%B8%B0-%EC%A0%9C%EC%96%B4)
