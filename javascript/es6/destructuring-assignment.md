# 비구조화 할당 \(destructuring assignment\)

객체 혹은 배열을 분해하여 필요한 필드만 추출하여, 별개의 변수로 대입하는 방식

## ES5

```javascript
var person1 = {
  name: "홍길동",
  age: 30,
  gender: "Male",
  skill: ["Java", "JavaScript", "Vue.js", "React"]
}

var name = person1.name;
var age = person1.age;

console.log(name, age); // 홍길동 30
```

## ES6

```javascript
let person1 = {
  name: "홍길동",
  age: 30,
  gender: "Male",
  skill: ["Java", "JavaScript", "Vue.js", "React"]
}

let { name, age, gender: ggg } = person1; 

console.log(name, age, ggg); // 홍길동 30 Male
```

```javascript
let person1 = {
  name: "홍길동",
  age: 30,
  gender: "Male",
  skill: ["Java", "JavaScript", "Vue.js", "React"]
}

function hello ({name}) {
  console.log(`Hello, ${name}`);
}

hello(person1); // Hello, 홍길
```

```javascript
let person1 = {
  name: "홍길동",
  age: 30,
  gender: "Male",
  skill: ["Java", "JavaScript", "Vue.js", "React"]
}

let [a, b, c] = person1.skill;

console.log(a, b, c); // Java JavaScript Vue.js
```

