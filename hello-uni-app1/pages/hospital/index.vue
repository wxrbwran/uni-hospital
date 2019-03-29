<template>
  <view class="hospital">
    <!-- <NavBar
      title="医院介绍"
      class="nav"
      left-arrow
      @click-left="onClickLeft"
    /> -->
    <view class="hospital__content">
			<image :src="hospitalBg" class="bg" mode="aspectFit"></image>
      <view class="hospital__info">
        <text class="title">
          <image :src="separated" mode="aspectFit" />
          医院简介
        </text>
        <text class="detail">{{ hospitalInfo }}</text>
      </view>
    </view>
  </view>
</template>
<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import separated from './img/separated.png';

@Component({
  components: {},
})
export default class Home extends Vue {
  separated:string = separated;

  get hospitalInfo() {
    // return this.$store.getters.info;
		return ''
  }

  get hospitalBg() {
    // return this.$store.getters.bg;
		return ''
  }

  onClickLeft() {
    // this.$router.push({ name: 'home' });
  }
}
</script>

<style lang="scss" scoped>
  .hospital{
    background-color: #fff;
  }
  .hospital__content{
    padding: 0 15px;
  }
  .bg{
    width: 100%;
    height: 152px;
    margin: 15px 0 20px;
  }
  .hospital__info{
  }
  .title{
    text-align: left;
    margin-bottom: 15px;
    position: relative;
    &:after{
      position: absolute;
      width: 230px;
      height: 1px;
      border: 1px solid #ebebeb;
    }
  }
  .detail{
    word-break: break-all;
    font-size: 13px;
    color: $help-text-color;
    letter-spacing: 0;
    text-align: justify;
    line-height: 21px;
  }
</style>
