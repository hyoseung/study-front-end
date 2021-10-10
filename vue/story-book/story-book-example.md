# 예제

Kendo UI Component를 이용하여 공통으로 사용할 수 있는 Dialog Component를 만든 후 storybook에 추가

참고 사이트 : [https://ipadorusa.com/posts/Storybook-vue-step03](https://ipadorusa.com/posts/Storybook-vue-step03)

### KendoDialog.vue

```javascript
<template>
  <Dialog :title="title" @close="$emit('close')" :width="dialogWidth">
    <slot name="content">
      default content
    </slot>
    
    <!-- 기본 dialogActionBar를 사용하지 않을 경우, <template #footer>로 커스터마징이하여 개발 -->
    <DialogActionsBar v-show="actionBarShow">
      <slot name="footer">
        <button class="k-button k-b-close" @click="$emit('close')">{{ closeBtnName }}</button>
        <button class="k-button k-b-confirm" @click="$emit('confirm')">{{ confirmBtnName }}</button>
      </slot>
    </DialogActionsBar>
    
  </Dialog>
</template>

<script>
import { Dialog, DialogActionsBar } from '@progress/kendo-vue-dialogs';

export default {
  components: {
    Dialog, DialogActionsBar
  },
  props: {
    title: { // :title="''"
      type: String,
      default: ''
    },
    closeBtnName: { // :close-btn-name="'취소'"
      type: String,
      default: "취소"
    },
    confirmBtnName: { // :confirm-btn-name="'확인'"
      type: String,
      default: "확인"
    },
    actionBarShow: { // :action-bar-show="true", close-btn-show와 confirm-btn-show 모두 false 하고 싶을 때는 action-bar-show=false 하는것을 추천
      type: Boolean,
      default: true
    },
    dialogWidth: {
      type: String,
      default: ''
    }
  }
}
</script>
```

### KendoDialog.stories.js

```javascript
import KendoDialog from "@/components/common/KendoDialog.vue";

export default {
  title: "개발/공통 Dialog",   // 스토리보드 제목
  component: KendoDialog,  // 스토리보드에 표시될 컴포넌트
  argTypes: { onClickConfirm: { action: 'clicked' } },
};

const Template = (args, { argTypes }) => ({ //스토리보드 좌측 이름 클릭시 보여지는 부분들
  components: { KendoDialog },
  props: Object.keys(argTypes),
  template: `
    <div>
      <button @click="visibleDialog = true" class="fillter-btn-active">click</button>
      <KendoDialog v-show="visibleDialog" v-bind="$props" @close="onClickClose" @confirm="onClickConfirm">
        <template #content>
          <div>content</div>
        </template>
      </KendoDialog>
    </div>
  `,
  data() {
    return {
      visibleDialog: false
    };
  },
  methods: {
    onClickClose() {
      this.visibleDialog = false;
    }
  }
});

export const FirstStory = Template.bind({});
FirstStory.args = {
  //title: "title"
};

```

### storybook

![첫 화면](<../../.gitbook/assets/image (35).png>)

!["click"버튼 클릭 후 > Dialog 보여짐](<../../.gitbook/assets/image (36).png>)

![Dialog에 "확인"버튼 클릭](<../../.gitbook/assets/image (37).png>)
