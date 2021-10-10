# 기본 파라미터 (Default Parameter)

## ES5

```javascript
function number(a, b, c) {
  console.log(a, b, c);
}

number(1); // 1 undefined undefined
```

## ES6

파라미터값에 기본값을 설정할 수 있음

```javascript
function number(a, b=2, c=3) {
  console.log(a, b, c);
}

number(1); // 1 2 3
```
