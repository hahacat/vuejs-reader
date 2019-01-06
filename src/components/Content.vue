<template>
  <transition name="slide-right">
    <div class="content">
      <div class="content-wrapper" v-if="bookAvailable">
        <div class="content-item" v-for="(item, index) in navigation.toc"
          :key="index"
          @click="jumpTo(item.href)">
          <span class="text">{{item.label}}</span>
        </div>
      </div>
      <div class="empty" v-else>加载中……</div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Content',
  props: {
    navigation: Object,
    ifShowContent: Boolean,
    bookAvailable: Boolean
  },
  methods: {
    jumpTo (href) {
      this.$emit('jumpTo', href)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/global';
.content {
  width: 70%;
  height: 100%;
  background: #fff;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 102;
  .content-wrapper {
    height: 100%;
    display: flex;
    flex-direction: column;
      .content-item {
        width: 100%;
        flex: 1;
        box-sizing: border-box;
        border-bottom: px2rem(1) dashed #ccc;
        span {
          display: block;
          height: 100%;
          font-size: px2rem(14);
          line-height: 100%;
        }
      }    
  }
  .empty {
    @include center;
    font-size: px2rem(14);
    line-height: 100%;
  }
}
</style>