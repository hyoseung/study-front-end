# 플렉서블 박스 속성

![](<../../../.gitbook/assets/image (44).png>)

## Flex Container

### display

부모 요소에 해당하는 Flex Container는 display 속성을 flex으로 설정하여 간단하게 Flex Container가 되며 직계 자식요소들은 Flex Item이 됨

수직과 수평 쌓임은 Item이 아니라 Container를 의미함

> #### flex
>
> * 박스를 블록 수준(수직 쌓임)의 플렉서블 박스로 작동하게 함
>
> #### inline-flex
>
> * 박스를 인라인 수준(수평 쌓임)의 플렉서블 박스로 작동하게 함

```css
.flex-container {
  display: -webkit-flex; /*웹 키트 계열 전용 접두사*/
  display:flex;
}
```

### flex-direction

Flex Item의 배치 방향을 설치하기 위함

> #### row (기본값)
>
> * Itmes를 수평축(왼쪽에서 오른쪽으로)으로 표시
> * 주축은 가로, 교차축은 세로
>
> #### row-reverse
>
> * row의 역방향으로(오른쪽에서 왼쪽으로) 표시
> * 주축은 가로, 교차축은 세로
>
> #### column
>
> * Items를 수직축(위에서 아래로)으로 표시
> * 주축은 세로, 교차축은 가로
>
> #### column-reverse
>
> * column의 역방향으로(아래서 위로) 표시
> * 주축은 세로, 교차축은 가로

```css
.flex-container{
  flex-direction : row | row-reverse | columns | column-reverse ;
}
```

### flex-wrap

Flex Item의 전체크기가 Flex Container 보다 클 때 Flex Item의 줄 바꿈 속성을 설정

Flex Item을 한줄(nowrap)로 표시할 지 여러줄로 (wrap)으로 표시 할지를 설정하게 됨

> #### nowrap (기본값)
>
> * items를 한줄로 배치
>
> #### wrap
>
> * items를 여러줄로 배치
>
> #### wrap-reverse
>
> * items를 여러줄로 배치하되, 역방향으로 배치

```css
.flex-container{
  flex-wrap: nowrap | wrap | wrap-reverse ;
}
```

### flex-flow

flex-direction과 flex-warp 두 속성property 의 간단 표기법

> #### \[flex-direction] \[flex-wrap]
>
> * row nowrap (기본값)

```css
.flex-container{
  flex-flow : flex-direction flex-wrap ;
}
```

### justify-content

주축을 따라 flex item 행을 정렬하는 방식 설정

> #### flex-start (기본값)
>
> * items을 주축의 시작점으로 정렬
>
> #### flex-end
>
> * items을 주축의 끝점으로 정렬
>
> #### center
>
> * items을 가운데 정렬
>
> #### space-between
>
> * 시작 item은 시작점에, 마지막 item은 끝점에 정렬, 나머지는 동일한 간격으로 정렬
> * Flex Container에 빈 공간이 있을 때 사용&#x20;
>
> #### space-around
>
> * itmes를 균등한 여백을 포함하여 정렬
> * Flex Container에 빈 공간이 있을 때 사용

```css
.flex-container{
  justify-content: flex-start | flex-end | center | space-between | space-around; 
}
```

### align-content

flex-wrap의 속성에 의해 여러 줄이 발생 했을 때 적용

align-item과 동시에 지정하였을 때 align-content과 우선

> #### stretch (기본값)
>
> * container의 교차축을 채우기 위해 items을 늘림
>
> #### flex-start
>
> * items을 주축의 시작점으로 정렬
>
> #### flex-end
>
> * items을 주축의 끝점으로 정렬
>
> #### center
>
> * items을 가운데 정렬
>
> #### space-between
>
> * 시작 item은 시작점에, 마지막 item은 끝점에 정렬, 나머지는 동일한 간격으로 정렬
> * Flex Container에 빈 공간이 있을 때 사용&#x20;
>
> #### space-around
>
> * itmes를 균등한 여백을 포함하여 정렬
> * Flex Container에 빈 공간이 있을 때 사용

```css
.flex-container{
  align-content: stretch | flex-start | flex-end | center | space-between | space-around;
}
```

### align-items

flex-wrap의 속성에 의해 여러 줄이 발생 했을 때 적용

align-item과 동시에 지정하였을 때 align-content과 우선

> #### stretch (기본값)
>
> * container의 교차축을 채우기 위해 items을 늘림
>
> #### flex-start
>
> * items을 교차축의 시작점으로 정렬
>
> #### flex-end
>
> * items을 교차축의 끝점으로 정렬
>
> #### center
>
> * items을 교차축의 중앙에 정렬
>
> #### baseline
>
> * items을 문자 기준선에 정렬

```css
.flex-container{
  align-items: stretch | flex-start | flex-end | center | baseline ;
}
```

## Flex Item

* flex item에 지정된 float 속성을 무시
* position:absolute 또는 position:fixed 속성이 설정되면 flex item에서 제외
* flex item은 형제 또는 부모의 수직 /수평 margin 속성이 중첩되지 않음

### order

Flex Item의 순서를 재배치 함

order값을 기본으로 오름차순으로 배치됨, 순서가 동일하면 소스코드 기준로 정해짐

> #### 0 (기본값)
>
> 정수값을 이용하여 지정 (0, 양수, 음수)

```css
.flex-item{
  oreder : <interger>;
}
```

### align-self

교차축을 방향으로 박스를 개별적으로 배치해야하는 경우 사용하는 속성값

교차축 margin이 auto로 설정되어있으면 align-self 효과가 없음

> #### auto (기본값)
>
> * 부모요소인 felx container에 지정된 align-items의 값을 가져옴
>
> #### stretch
>
> * flex item의 높이는 flex container 내 flex item행의 최대 높이로 지정됨
> * flext item 행이 하나 일때는 flex item은 교차축 방향으로 flex container를 가득 채움
>
> #### flex-start
>
> * 교차축의 시작선부터 flext item을 정렬
>
> #### flex-end
>
> * 교차축의 끝선에 flex item 마지막 항목이 오게 정렬
>
> #### center
>
> * 교차축의 가운데에 flex item을 정렬
>
> #### baseline
>
> * flex item을 문자의 기준선에 맞게 정렬

```css
.flex-item{
  align-self: auto | stretch | flex-start | flex-end | center | baseline ;
}
```

### flex-grow

flex container에 여백이 있을 때 flex item의 크기를 늘일 수 있는 속성 (확장여부 결정)

속성값은 비율로 설정, 음수값은 사용할 수 없음

> #### 0 (기본값)
>
> * flex item을 확장하지 않음
>
> #### 1
>
> * flex item의 너비를 flex container 내부에 남은 공간에 채워지도록 각 item에 분배하여 너비를 확장
>
> #### 양의 정수
>
> * number 값이 클수록 확장 지수를 커짐
>
> #### flex item 크기
>
> * 박스 기본 크기 + (free space / 팽창지수 총합) \* flex-grow값

```css
.flex-item{
  flex-grow:number;
}
```

### flex-shrink

flex container의 공간이 부족할 때 flex item의 크기를 줄이는 방법

속성값은 비율로 설정, 음수값은 사용할 수 없음

> #### 0 (기본값)
>
> * flex item을 축소하지 않음
>
> #### 1
>
> * flex item의 너비를 flex container 내부에 맞게 item의 크기를 축소함
>
> #### 양의 정수
>
> * number 값이 클수록 축소 지수를 커짐
>
> #### flex item 크기
>
> * 박스 기본 크기 + (free space / 수축지수 총합) \* flex-shrink값

```css
.flex-item{
  flex-shrink:number;
}
```

