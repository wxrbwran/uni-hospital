<template>
  <view class="home">
    <!-- <NavBar class="nav" title="首页" /> -->
    <view class="home-content">
      <view class="welcome">
        <view><text class="hi">hi, 欢迎您</text></view>
        <text>欢迎来到<text class="name">【{{ hospitalName }}】</text>,以下入口为您引导看病</text>
      </view>
      <view class="img-content">
        <image class="bg" :src='hospitalBg' />
        <view class="note">
          <image :src='hospitalLogo' class="note-logo"/>
          <view class="note-text">
            <text>{{ hospitalName }}互联网医院</text>
            <text>花最少的钱  看最好的医生</text>
          </view>
        </view>
      </view>
      <view class="service">
        <text class="">主打服务</text>
				<view class="uni-product-list service-list">
					<view
					 class="uni-product service-list__item"
					 v-for="(service,index) in services"
					 :key="index"
				 >
						<view class="title"><text>{{ service.title }}</text></view>
						<view class="extra"><text>{{ service.extra }}</text></view>
						<image :src="service.icon" mode="aspectFit"></image>
					</view>
				</view>
      </view>
      <view class="footer">
        <text>专业的互联网医院门诊部 让您不再找医生感觉困难啦~~...</text>
      </view>
    </view>
  </view>
</template>
<script>
import { Vue } from 'vue';
// import { NavBar } from 'vant';
import outpatient from './img/outpatient_service.png';
import slow from './img/slow_disease.png';
import referral from './img/referral.png';
import introduce from './img/hospital_introduced.png';

export default {
	computed: {
		services() {
		  return [
		    {
		      title: '门诊',
		      extra: '60s快速回复',
		      icon: outpatient,
		    },
		    {
		      title: '慢病管理',
		      extra: '自己的贴身管家',
		      icon: slow,
		      fn: () => {
		      },
		    },
		    {
		      title: '转诊/会诊',
		      extra: '会诊转诊快捷',
		      icon: referral,
		    },
		    {
		      title: '医院介绍',
		      extra: `${this.hospitalName}名医`,
		      icon: introduce,
		      fn: () => {
		      },
		    },
		  ];
		},
		hospitalName() {
		  // return this.$store.getters.name;
			return '';
		},
		hospitalLogo() {
		  // return this.$store.getters.logo;
			return '';
		},
		hospitalBg() {
		  // return this.$store.getters.bg;
			return '';
		}
	},
  created() {
    if (!this.hospitalLogo) {
    // console.log(this.$route);
      // const { id } = this.$route.query;
      // this.$store.dispatch('fetchHospitalInfo', id);
    }
  },
  handleServeClick(fn) {
    if (fn) { fn(); }
  }
}
</script>

<style lang="scss" scoped>
  $pic-color: #327EC1;
  .home{
    text-align: left;
    background-color: #fff;
  }
  .home-content{
    padding: 0 30upx;
    .welcome{
      color: $main-text-color;
      padding: 28upx ;
      .hi{
        font-size: 40upx;
        line-height: 40upx;
        margin-bottom: 26upx;
      }
      .name{
        font-size: 28upx;
        line-height: 28upx;
        span{
          color: #1d0000;
          font-weight: bold;
        }
      }
    }
  }
  .img-content{
    width: 100%;
    height: 304upx;
    position: relative;
    .bg{
      width: 100%;
      height: 304upx;
    }
    .note{
      position: absolute;
      top: 60upx;
      left: 16upx;
      color: $pic-color;
      @include flex(row, nowrap, flex-start, center);
      &-logo{
        @include size(60upx);
        margin-right: 6upx;
      }
    }
    .note-text{
      text{
        font-size: 36upx;
      }
      p{
        font-size: 24upx;
        margin-top: 6upx;
        /*transform: scale(0.5);*/
      }
    }
  }
  .service{
    > text{
      font-size: 34upx;
      color: $main-text-color;
      font-weight: bold;
      margin: 68upx auto 36upx;
      text-align: center;
    }
    &-list{
      @include flex(row, wrap, flex-start, flex-start);
      &__item{
        width: 336upx;
        height: 240upx;
        margin-bottom: 18upx;
        overflow: hidden;
        background: #f8fbfe left top no-repeat;
        background-size: cover;
        &:nth-child(1),
        &:nth-child(3) {
          margin-right: 18upx;
        }
        > .title {
          text-indent: 24upx;
          color: $main-text-color;
          font-size: 34upx;
          margin: 46upx 0 12upx;
        }
        > .extra{
          text-indent: 24upx;
          font-size: 24upx;
          color: $help-text-color;
        }
      }
    }
  }
  .footer{
    margin-top: 36upx;
    text-align: center;
    font-size: 24upx;
    color: #ABACAD;
    padding-bottom: 28upx;
  }
</style>
