<template>
	<div class="download"
    :style="{backgroundImage: `url(${background})`}"
  >
    <img
      :src="back"
      class="back"
      alt=""
      @click="onClickLeft"
    >
    <div class="app-info">
      <img :src="logo" class="logo" alt="">
      <p>心之力</p>
      <img :src="slogan" class="slogan" alt="">
    </div>
    <div class="download__btn">
      <div class="device-item">
        <img :src="android" alt="">
        <a
          href="https://revomedi.cn/xinzhili-android-app"
          target="_blank"
        >Android版下载</a>
      </div>
      <div class="device-item">
        <img :src="iPhone" alt="">
        <a
          href="https://itunes.apple.com/cn/app/id1423445984?mt=8"
          target="_blank"
        >iPhone版下载</a>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { NavBar } from 'vant';
import back from './img/back.png';
import logo from './img/logo.png';
import slogan from './img/slogan.png';
import background from './img/background.png';
import android from './img/android.svg';
import iPhone from './img/iPhone.svg';

@Component({
  components: {
    NavBar,
  },
})
export default class Home extends Vue {
  back:string = back;
  logo:string = logo;
  slogan:string = slogan;
  background:string = background;
  android:string = android;
  iPhone:string = iPhone;
  onClickLeft():void {
    this.$router.push({ name: 'home' });
  }
}
</script>

<style lang="scss" scoped>
  .download{
    position: absolute;
    width: 100%;
    height: 100%;
    background: #fff left bottom no-repeat;
    background-size: contain;
    .back{
      position: absolute;
      left: 20px;
      top: 17px;
      @include size(16px);
    }
    .app-info{
      margin-top: 32px;
      @include flex(column, nowrap, flex-start, center);
      .logo{
        @include size(60px, 67px);
      }
      p{
        font-size: 13px;
        color: #181818;
        font-weight: bold;
        margin-bottom: 32px;
      }
    }
    .download__btn{
      @include flex(column, nowrap, flex-start, center);
      width: 100%;
      color: #fff;
      position: absolute;
      bottom: 70px;
      left: 0;
      text-align: center;
    }
    .device-item{
      width: 180px;
      height: 50px;
      border: 1px solid #fff;
      border-radius: 27.5px;
      @include flex(row, nowrap, center, center);
      a{
        color: #fff;
      }
      img{
        margin-right: 14px;
      }
      &:first-child{
        margin-bottom: 20px;
      }
    }
  }
</style>
