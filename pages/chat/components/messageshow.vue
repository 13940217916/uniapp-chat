<template>
  <view class="m-item" :id="'message' + id">
    <view class="m-left">
      <image
        class="head_icon"
        :src="abosultPaht + user.home.img"
        v-if="message.user === 'home'"
      ></image>
    </view>
    <view class="m-content">
      <view
        class="m-content-head"
        :class="{ 'm-content-head-right': message.user === 'customer' }"
      >
        <view :class="'m-content-head-' + message.user"
          >{{ message.content }}
        </view>
      </view>
    </view>
    <view class="m-right">
      <image
        class="head_icon"
        :src="abosultPaht + user.customer.img"
        v-if="message.user === 'customer'"
      ></image>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      abosultPaht: "../../",
      user: {
        home: {
          id: 1,
          name: "tax",
          img: "static/img/headimg.png",
        },
        customer: {
          id: 2,
          name: "customer",
          img: "static/img/headimg1.png",
        },
      },
    };
  },
  props: ["message", "id"]
};
</script>

<style>
.m-item {
  display: flex;
  flex-direction: row;
  padding-top: 40px;
}
.m-left {
  display: flex;
  width: 120rpx;
  justify-content: center;
  align-items: flex-start;
}
.m-content {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  word-break: break-all;
}
.m-right {
  display: flex;
  width: 120rpx;
  justify-content: center;
  align-items: flex-start;
}
.head_icon {
  width: 80rpx;
  height: 80rpx;
  border-radius: 10rpx;
  overflow: hidden;
  background-color: #fff;
}
.m-content-head {
  position: relative;
}
.m-content-head-right {
  display: flex;
  justify-content: flex-end;
}
.m-content-head-home {
  text-align: left;
  background: #35AEAC;
  border: 1px #35AEAC solid;
  border-radius: 20rpx;
  padding: 20rpx;
  color: white;
}
.m-content-head-home:before {
  border: 15px solid transparent;
  border-right: 15px solid #35AEAC;
  left: -42rpx;
  top:10rpx;
  width: 0;
  height: 0;
  position: absolute;
  content: " ";
}
.m-content-head-customer {
  border: 1px white solid;
  background: #343643;
  border-radius: 20rpx;
  padding: 20rpx;
  color: #fff;
}
.m-content-head-customer:after {
  border: 15px solid transparent;
  border-left: 15px solid #343643;
  top: 20rpx;
  right: -40rpx;
  width: 0;
  height: 0;
  position: absolute;
  content: " ";
}
</style>
