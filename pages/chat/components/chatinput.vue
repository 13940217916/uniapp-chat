<template>
  <view class="footer">
    <view class="footer-center">
      <input
        class="input-text"
        :focus="true"
        type="text"
        v-bind:value="inputValue"
        @input="$emit('input', $event.target.value)"
        placeholder=""
        :maxlength="250"
        confirm-type="send"
        confirm-hold
        @keydown.enter="sendMessge"
      />
    </view>
    <view class="footer-right">
      <u-image
        width="60rpx"
        height="60rpx"
        :src="require('@/static/svg/chat-small.svg')"
        @click="$emit('showEmjoy')"
      ></u-image>
      <u-image
        width="60rpx"
        height="60rpx"
        :src="require('@/static/svg/chat-add.svg')"
        v-show="!inputValue"
      ></u-image>
      <view class="send-btn" v-show="inputValue" @tap="sendMessge">发送</view>
    </view>
  </view>
</template>

<script>
export default {
  name: "chat-input",
  model:{
    prop:'inputValue',
    event:'input'
  },
  props:{
    inputValue:[String,Number]
  },
  methods: {
    sendMessge() {
      var that = this;
      if (that.inputValue.trim() === "") {
        this.$emit('input', "")
      } else {
        //点击发送按钮时，通知父组件用户输入的内容
        this.$emit("send-message", {
          type: "text",
          content: that.inputValue,
        });
        this.$emit('input', "")
      }
    },
  },
};
</script>

<style>
.footer {
  display: flex;
  flex-direction: row;
  width: 100%;
  border-top: solid 1px #bbb;
  overflow: hidden;
  height:100rpx;
}
.footer-right {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-left: 20rpx;
}
.footer-center {
  flex: 3;
  display: flex;
  justify-content: center;
  align-items: center;
}
.footer-center .input-text {
  background: #f5f4f7;
  overflow: hidden;
  width: 100%;
  height: 100%;
}
.send-btn {
  padding: 10rpx 15rpx;
  margin-left: 10rpx;
  background-color: #35aeac;
  color: #fff;
  text-align: center;
  border-radius: 5rpx;
}
</style>
