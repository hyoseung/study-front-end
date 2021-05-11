# 템플릿 리터럴 \(Template literal\)

역따옴표\(\`\)로 묶여진 문자열에서 템플릿 대입문\(${}\)을 이용해 동적으로 문자열을 끼워넣어 구성할 수 있음

## ES5

```javascript
let name = '홍길동';
let age = 30;

console.log(name+"의 나이는 "+age+"살 입니다.");
// 홍길동의 나이는 30살 입니다.
```

## ES6

```javascript
let name = '홍길동';
let age = 30;

console.log(`${name}의 나이는 ${age}살 입니다.`);
// 홍길동의 나이는 30살 입니다.

console.log(`${name}의 
나이는 ${age}살 입니다.`);
// 홍길동의 
// 나이는 30살 입니다.
```

