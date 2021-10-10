# 뷰포트

## 뷰포트란?

* 화면에 보이는 영역을 제어하는 기술
* 미디어 쿼리로 수많은 기기의 화면 크기를 감지해야 할 때 필요
* 스마트 기기의 보이는 영역을 기기의 실제 화면 크기로 변경하여 미디어 쿼리가 기기의 화면 크기를 정확하게 감지할 수 있도록 하기 위해 뷰포트 기술 사용 (데스크톱은 사용자가 지정한 해상도에 따라 보이는 영역이 결정, 스마트 기기는 기본 설정값이 자동으로 보이는 영역으로 설정)

```html
<!DOCTYPE HTML>
<html lang="ko">
<head>
<meta charset="UTF-8">
<!-- viewport -->
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
<title>Document</title>
</head>
<body>
</body>
</html>
```

## 뷰포트 속성

| 속성명           | 속성값                | 설명                                                                                     |
| ------------- | ------------------ | -------------------------------------------------------------------------------------- |
| width         | device-width, 양수   | 너비                                                                                     |
| heigth        | device-height, 양수  | 높이                                                                                     |
| initial-scale | 양수                 | <p>초기 배율지정, 기본값 1 </p><p>1 > 축소된 페이지 표시</p><p>1 &#x3C; 확대된 페이지 표시</p><p>0~10 사이의 값</p> |
| user-scalable | yes, no            | 확대/축소 여부, 기본값 yes                                                                      |
| minimum-scale | 양수                 | <p>최소 축소 비율, 기본값 0.25</p><p>0~10 사이의 값</p>                                             |
| maximum-scale | 양수                 | <p>최대 확대 비율, 기본값 5.0</p><p>0~10 사이의 값</p>                                              |

## 출처

* Do it! 반응형 웹 페이지 만들기 | 김운아 | 이지스퍼블리싱

