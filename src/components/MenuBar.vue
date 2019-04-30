<template>
<div class="menuBar">
     <transition name="slide-up">
    <div class="menu-wrapper" v-show="isShow">
        <div class="icon-wrapper">
            <span class="iconfont icon-menu"></span>
        </div>
         <div class="icon-wrapper">
            <span class="iconfont icon-Progressread"></span>
        </div>
         <div class="icon-wrapper">
            <span class="iconfont icon-brightness"></span>
        </div>
         <div class="icon-wrapper">
            <span class="iconfont icon" @click="toggleFontSize">A</span>
        </div>
    </div>
    </transition>
    <transition name="slide-up">
    <div class="setting-wrapper" v-show="isFontSizeShow">
        <div class="setting-font-size"></div>
    </div>
    </transition>

</div>
</template>

<script>
    export default {
       props:{
            isShow: {
                type: Boolean,
                default: false
            }
        },data(){
            return{
                isFontSizeShow:false
            }
        },methods :{
            toggleFontSize:function(){
                  this.isFontSizeShow = !this.isFontSizeShow;
            },hideSettingFontSize:function(){
                this.isFontSizeShow = false;
            }
        }
    }
</script>

<style lang="scss" scoped>
@import '../assets/styles/global';
.menuBar{
    .menu-wrapper{
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    z-index: 101;
    background-color: white;
    height: px2rem(48);
    display: flex;
    box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);
    .icon-wrapper{
        flex: 1;
        @include center;
        .icon-menu{
            font-size: px2rem(22);
        }
        .icon-Progressread{
            font-size: px2rem(22);
        }
        .icon-brightness{
            font-size: px2rem(22);
        }
    }
  }
  .setting-wrapper{
    position: absolute;
    bottom: px2rem(48);
    left: 0;
    width: 100%;
    z-index: 101;
    background-color: yellow;
    height: px2rem(60);
    display: flex;
    box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);
  }
}

</style>