<template>
    <transition name="slide-down">
    <div class="title-wrapper" v-show="isShow">
      <div class="left">
        <span class="icon iconfont icon-back"></span>
      </div>
      <div class="right">
        <div class="icon-wrapper">
          <span class="icon iconfont icon-cart-copy"></span>
        </div>
        <div class="icon-wrapper">
          <span class="icon iconfont icon-person"></span>
        </div>
        <div class="icon-wrapper">
          <span class="icon iconfont icon-Progressread"></span>
        </div>
      </div>
    </div>
    </transition>
</template>

<script>
    export default {
         props:{
            isShow: {
                type: Boolean,
                default: false
            }
        }
    }
</script>

<style lang="scss" scoped>
@import '../assets/styles/global';
 .title-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 101;
    background-color: white;
    height: px2rem(48);
    display: flex;
    box-shadow: 0 px2rem(8) px2rem(8) rgba(0, 0, 0, 0.15);
    .left {
      flex: 0 0 px2rem(60);
      @include center();
    }
    .right {
      flex: 1;
      display: flex;
      justify-content: flex-end;
      .icon-wrapper {
        flex: 0 0 px2rem(40);
        @include center;
        .icon-cart-copy{
            font-size: px2rem(22)
        }
      }
    }
  }

</style>