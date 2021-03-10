<template>
  <view class="content">
    <view
      v-for="(item, index) in emjoyArr"
      :key="index"
      class="item"
      @click="choose(item)"
      >{{ item }}</view
    >
  </view>
</template>
<script>
import { emjoyArr } from "../emjoydata";
export default {
  data() {
    return {
      emjoyArr,
    };
  },
  methods: {
    choose(item) {
      this.$emit("choose", item);
    },
  },
};
</script>
<style scoped lang="scss">
.content {
  display: flex;
  flex-wrap: wrap;
  height: 400rpx;
  overflow-y: auto;
  .item {
    padding: 8rpx 5rpx;
  }
}
</style>