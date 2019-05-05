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
        <div class="setting-font-size">
          <div class="preview" :style="{fontSize: fontSizeList[0].fontSize+'px'}">A</div>
          <div class="select">
            <div class="select-wrapper" v-for="(item,index) in fontSizeList" :key="index" @click="setFontSize(item.fontSize)">
              <div class="line"></div>
              <div class="point-wrapper" >
                <div class="point" v-show="defalutFontSize===item.fontSize">
                    <div class="small-point"></div>
                </div>
              </div>
              <div class="line"></div>
            </div>
          </div>
          <div
            class="preview"
            :style="{fontSize: fontSizeList[fontSizeList.length-1].fontSize+'px'}"
          >A</div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    isShow: {
      type: Boolean,
      default: false
    },
    fontSizeList: {
      type: Array
    },
    defalutFontSize: {
        type: Number
    }
  },
  data() {
    return {
      isFontSizeShow: false
    };
  },
  methods: {
      setFontSize:function(fontSize){
            this.$emit("setFontSize",fontSize)
      },
    toggleFontSize: function() {
      this.isFontSizeShow = !this.isFontSizeShow;
    },
    hideSettingFontSize: function() {
      this.isFontSizeShow = false;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/styles/global";
.menuBar {
  .menu-wrapper {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    z-index: 101;
    background-color: white;
    height: px2rem(48);
    display: flex;
    box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);
    .icon-wrapper {
      flex: 1;
      @include center;
      .icon-menu {
        font-size: px2rem(22);
      }
      .icon-Progressread {
        font-size: px2rem(22);
      }
      .icon-brightness {
        font-size: px2rem(22);
      }
    }
  }

  .setting-wrapper {
    position: absolute;
    bottom: px2rem(48);
    left: 0;
    width: 100%;
    z-index: 101;
    background-color: white;
    height: px2rem(60);
    box-shadow: 0 px2rem(-8) px2rem(8) rgba(0, 0, 0, 0.15);
    .setting-font-size {
      display: flex;
      height: 100%;
      .preview {
        flex: 0 0 px2rem(40);
        @include center;
      }
      .select {
          display: flex;
          flex: 1;
        .select-wrapper {
            display: flex;
            flex: 1;
            align-items: center;
             &:first-child {
            .line {
              &:first-child {
                border-top: none;
              }
            }
          }
          &:last-child {
            .line {
              &:last-child {
                border-top: none;
              }
            }
          }
            .line {
            flex: 1;
            height: 0;
            border-top: px2rem(1) solid #ccc;
          }
          .point-wrapper {
               flex: 0 0 0;
                width: 0;
                height: px2rem(7);
                border-left: px2rem(1) solid #ccc;
            .point {
                position: relative;
               top: px2rem(-8);
              left: px2rem(-10);
              width: px2rem(20);
              height: px2rem(20);
              border-radius: 50%;
               background: white;
              border: px2rem(1) solid #ccc;
              box-shadow: 0 px2rem(4) px2rem(4) rgba(0, 0, 0, .15);
              @include center;
               
                .small-point{
                    position: absolute;
                    width: px2rem(5);
                height: px2rem(5);
                background: black;
                border-radius: 50%;
              }
            }
          }
        }
      }
    }
  }
}
</style>