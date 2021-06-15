# 예제

## sass 설치

```text
npm insatll -g sass
```

## sass -&gt; css로 컴파일

```text
sass test.scss test.css
```

## 예제

```markup
<!DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title>Document</title>
<link rel="stylesheet" href="./scss/test.css">
</head>
<body>
	<div id="wrap">
		<div class="container">
			<div></div><div></div>
		</div>
	</div>
</body>
```

```css
// test.scss

*{margin:0; padding:0;}
#wrap {
	width: 90%; /*960px, 임의설정->미리 정해둔 목적 또는 크기를 최상위 박스의 너비값으로 함*/
	height: 500px;
	margin: 0 auto;
	border: 4px solid #000;
}
.container {
	width: 93.75%; /* 900px/960px*100 */
	height: 492px;
	margin: 0 auto;
	border: 4px solid #000;

	div {
		height:100%;
		display:inline-block;
    &:first-child {
      width: 33.3%;
      background:#1f518b;
    }
    &:first-child + div {
      width: 66.6%;
      background:#f7e041;
    }
	}
}
```

