<template>
  <div class="ebook">
    <title-bar :isShow="isShow"></title-bar>
    <div class="read-wrapper">
      <div id="read"></div>
      <div class="mask">
        <div class="left" @click="prevPage"></div>
        <div class="center" @click="toggleTitleAndMenu"></div>
        <div class="right" @click="nextPage"></div>
      </div>
    </div>
    <menu-bar :isShow="isShow" ref="MenuBar"></menu-bar>
  </div>
</template>

<script>
import TitleBar from '@/components/TitleBar'
import MenuBar from '@/components/MenuBar'
import Epub from "epubjs";
const DOWNLOAD_URL = "/static/2018_Book_AgileProcessesInSoftwareEngine.epub";
global.ePub = Epub;
export default {
    components:{
     TitleBar,
     MenuBar
    },
    data(){
        return{
     isShow:false
        }
    },
  methods: {
    //电子书的解析和渲染
    showEpub() {
      //生成Book对象
      this.book = new Epub(DOWNLOAD_URL);
      //生成Rendition对象,通过Book.renderTo生成
      this.rendition = this.book.renderTo("read", {
        width: window.innerWidth,
        height: window.innerHeight
      });
      //通过Rendition.display渲染电子书
      this.rendition.display();
    },
    prevPage() {
      console.log(this.rendition);
      if(this.isShow){
          this.isShow = false;
          return;
      }
      if (this.rendition) {
        this.rendition.prev();
      }
    },
    nextPage() {
      console.log(this.rendition);
      if(this.isShow){
          this.isShow = false;
          return;
      }
      if (this.rendition) {
        this.rendition.next();
      }
    },toggleTitleAndMenu(){
        this.isShow = !this.isShow;
        if(!this.isShow){
           this.$refs.MenuBar.hideSettingFontSize();
        }
    }
  },
  mounted() {
    this.showEpub();
  }
};
</script>

<style lang='scss' scoped>
@import "assets/styles/global";
.ebook {
  position: relative;
 .read-wrapper {
    .mask {
      position: absolute;
      top: 0;
      left: 0;
      z-index: 100;
      display: flex;
      width: 100%;
      height: 100%;
      .left {
        flex: 0 0 px2rem(100);
      }
      .center {
        flex: 1;
      }
      .right {
        flex: 0 0 px2rem(100);
      }
    }
  }
}
</style>