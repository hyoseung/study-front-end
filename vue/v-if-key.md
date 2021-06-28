# v-if key

## `v-if`, `v-else-if`, `v-else` 에 `key`를 사용하는 이유

* Vue는 효율적인 렌더링을 위해 때때로는 처음부터 렌드링을 하지않고 기존의 엘리먼트를 다시 사용
* key를 사용하면 재사용 가능한 엘리먼트를 제어할 수 있음

### `key`를 사용하지 않았을 경우

```markup
<div id="app">
  <div>
    <template v-if="loginType === 'username'">
      <label>사용자 이름</label>
      <input placeholder="사용자 이름을 입력하세요">
    </template>
    
    <template v-else>
      <label>이메일</label>
     <input placeholder="이메일 주소를 입력하세요">
    </template>
    
    <button @click="changeLoginType">로그인 유형 변경</button>
  </div>
</div>
```

* `changeLogingType` : logingType을 'username' or 'email'로 변경하는 메서드
* 위 코드를 실행하여 input에 데이터를 입력하고 loginType을 변경해도 사용자가 입력한 내용은 지워지지않음
* Vue는 엘리먼트를 재사용할 수 있어 `<input>` 자체가 대체되지 않고, `placeholder`만 변경됨

### `key` 사용할 경우

* 엘리먼트를 재사용하지 않기를 원하면 `key` 속성을 사용
* `key` 속성을 사용하면 완전 별개의 엘리먼트인 것을 명시하면 Vue는 엘리먼트를 재사용하지않고 완전히 대체하여 렌더링 됨

```markup
<div id="app">
  <div>
    <template v-if="loginType === 'username'">
      <label>사용자 이름</label>
      <input placeholder="사용자 이름을 입력하세요" key="username-input">
    </template>
    
    <template v-else>
      <label>이메일</label>
     <input placeholder="이메일 주소를 입력하세요" key="email-input">
    </template>
    
    <button @click="changeLoginType">로그인 유형 변경</button>
  </div>
</div>
```

* 참고 예제 - CodePen : [https://codepen.io/beomy/pen/BGwgBJ?editors=1010](https://codepen.io/beomy/pen/BGwgBJ?editors=1010)

## 출처

* [버미노트 \| 2018. 11. 20. 00:36 \| \[Vue.JS\] 조건부 렌더링](https://beomy.tistory.com/51)

