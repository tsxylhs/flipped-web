<template >
  <view class="container">
  
    <!--轮播图-->
    <uni-swiper-dot class="uni-swiper-dot-box" @clickItem=clickItem :info="info" :current="current" :mode="mode"
      :dots-styles="dotsStyles" field="content">
      <swiper class="swiper-box" @change="changeImage" :current="swiperDotIndex">
        <swiper-item v-for="(item, index) in info" :key="index">
          <view class="swiper-item" :class="'swiper-item' + index">
            <image :src="item.url" class="image" mode="aspectFill" />
          </view>
        </swiper-item>
      </swiper>
    </uni-swiper-dot>

    <swiper class="swiper-box1" :indicator-dots="false">
      <swiper-item v-for="(topic, index) in topics">
        <uni-grid :highlight="false" :showBorder="false" :column="5"  @change="change">
          <uni-grid-item   v-for="(item, index) in topic" :index="index" :key="index">
            
            <view >
              <cover-image class="grid-item-image" mode="aspectFill" :src="item.url"  >
              </cover-image>
          </view>
          <view><text class="text">{{ item.topicName }}</text></view>
          </uni-grid-item>
        </uni-grid>
      </swiper-item>
    </swiper>
    <uni-grid :highlight="false"  :showBorder="false" :column="2" @change="change">
      <uni-grid-item  v-for="(item, index) in list" :index="index" :key="index">
        <view class="grid-item-box">
  
          <cover-image  class="image-radius" :src="item.url" mode="aspectFill" />
    
        <view class="text-style">{{ item.text }}</view>
     
      
        </view>
      </uni-grid-item>
    </uni-grid>

    <!--悬浮框--->
  </view>
  
</template>

<script>
import { Warning } from 'postcss'

export default {
  data() {

    return {
      //轮播图
      mode: 'nav',
      current: 0,

      info: [{
        colorClass: 'uni-bg-red',
        url: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
        content: '春节线下相亲会A'
      },
      {
        colorClass: 'uni-bg-green',
        url: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
        content: '春节线下相亲会B'
      },
      {
        colorClass: 'uni-bg-blue',
        url: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
        content: '春节线下相亲会C'
      }
      ],
      dotsStyles: {
        backgroundColor: 'rgba(255, 90, 95,0.3)',
        border: '1px rgba(255, 90, 95,0.3) solid',
        color: '#fff',
        selectedBackgroundColor: 'rgba(255, 90, 95,0.9)',
        selectedBorder: '1px rgba(255, 90, 95,0.9) solid'
      },

     
  

      topics: [[{
        url: "/static/xiangcun.jpg",
        id: "1",
        topicName: "跨年计划"
      }, {
        url: "/static/xiaoyuan.jpg",
        id: "2"
        ,
        topicName: "春节相亲"
      }, {
        url: "/static/xiaoyuan.jpg",
        id: "3"
        ,
        topicName: "话题3"
      }, {
        url: "/static/xiaoyuan.jpg",
        
        topicName: "话题4"
      }, {
         url: "/static/xiaoyuan.jpg",
        
        topicName: "话题5"
      }],
      [{
        url: "/static/add.png",
        id: "2-1",
        topicName: ""
      }, {
        url: "/static/add.png",
        id: "2-2",
        topicName: ""
      }, {
        url: "/static/add.png",
        id: "2-3",
        topicName: ""
      }, {
        url: "/static/add.png", id: "4",
        topicName: ""
      }, {
        url: "/static/add.png", id: "4"
        ,
        topicName: "话题5"
      }]
      ],
      //grid
      list: [{
        url: "/static/xiaoyuan.jpg",
        text: "校园"
      }, {
        url: "/static/xiangcun.jpg",
        text: "乡村"
      }, {
        url: "/static/shechu.jpg",
        text: "社畜"
      }, {
        url: "/static/xin.png",
        text: "同城"
      }]
    }
  },
  onLoad() { },
  onBackPress() {
    if (this.$refs.fab.isShow) {
      this.$refs.fab.close()
      return true
    }
    return false
  },
  methods: {
    clickItem(e) {
      this.swiperDotIndex = e
    },
    back() { },

    changeGrid(e) { },
    changeImage(e) {
      this.current = e.detail.current
    },
    trigger(e) {
      console.log(e)
      this.content[e.index].active = !e.item.active
      // uni.showModal({
      // 	title: '提示',
      // 	content: `您${this.content[e.index].active ? '选中了' : '取消了'}${e.item.text}`,
      // 	success: function(res) {
      // 		if (res.confirm) {
      // 			console.log('用户点击确定')
      // 		} else if (res.cancel) {
      // 			console.log('用户点击取消')
      // 		}
      // 	}
      // })
    },
  },
}
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
  background-color: lightcoral;
}

.warp {
  padding: 10px;
}

.button {
  margin-bottom: 10px;
}

.text-area {
  display: flex;
  justify-content: center;
}

.swiper {
  display: block;
  height: 140px;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}

.grid-item {
  width: 85%;
  height: 85%;
  margin-top: 5px;
  border-radius: 150px 150px 150px 150px;
  background: rgb(157, 35, 143);
  opacity: 1;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}

.grid-item-box {
  width: 95%;
  height: 95%;
  margin-top: 5px;
  margin-left: 5px;
  border-radius: 30px 30px 30px 30px;
  background: rgb(157, 35, 143);
  opacity: 1;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}
.image-radius{
  width: 100%; height: 100%;
  border-radius: 30px 30px 30px 30px;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}
.text {


  color: rgb(199, 55, 55);
  font-size: 20upx;
  margin-left: 3vh;
  text-align: center;


}

.test2 {
  background-image: linear-gradient(red 10%, yellow, green, orange);
  background-size: 100vh 100ch;
}

.img {
  position: static;
  top: -50%;
  left: -50%;
  vertical-align: middle;
}

.swiper-box {
  height: 26vh;
}

.swiper-box1 {
  height: 16vh;
}

.swiper-item {
  /* #ifndef APP-NVUE */
  display: flex;
  /* #endif */
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 200px;
  color: #fff;
}
.grid-item-image{
  width: 10vh;
  height: 10vh;
  margin-top: 1vh;
  margin-left: 1vh;
  border-style: double;
  border-color:#eb49a4;
  border-radius: 120px 120px 120px 120px;
  opacity: 1;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}
.swiper-item0 {
  background-color: #cee1fd;
}

.swiper-item1 {
  background-color: #b2cef7;
}


.swiper-item2 {
  background-color: #cee1fd;
}

.image {
  width: 750rpx;

}

/* #ifndef APP-NVUE */
::v-deep .image img {
  -webkit-user-drag: none;
  -khtml-user-drag: none;
  -moz-user-drag: none;
  -o-user-drag: none;
  user-drag: none;
}

/* #endif */

@media screen and (min-width: 500px) {
  .uni-swiper-dot-box {
    width: 400px;
    margin: 0 auto;
    margin-top: 8px;
  }

  .image {
    width: 100%;
  }
}

.uni-bg-red {
  background-color: #ff5a5f;
}

.uni-bg-green {
  background-color:#7A90F9;
}

.uni-bg-blue {
  background-color: #007aff;
}

.example-body {
  /* #ifndef APP-NVUE */
  display: flex;
  /* #endif */
  flex-direction: row;
  padding: 20rpx;
}

.example-body-item {

  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin: 15rpx;
  padding: 15rpx;
  height: 60rpx;
  /* #ifndef APP-NVUE */
  display: flex;
  padding: 0 15rpx;
  /* #endif */
  flex: 1;
  border-color: #e5e5e5;
  border-style: solid;
  border-width: 1px;
  border-radius: 5px;
}

.example-body-item-text {
  font-size: 28rpx;
  color: #333;
}

.topicImage {
  width: 30PX;
  height: 30px;
}

.example-body-dots {
  width: 16rpx;
  height: 16rpx;
  border-radius: 50px;
  background-color: #333333;
  margin-left: 10rpx;
}
.text-style {
					position: absolute;
					top: 240upx;
					left: 20upx;
					font-size: 70upx;
					color: #FFFFFF;
}
.active {
  border-style: solid;
  border-color: #007aff;
  border-width: 1px;
}
</style>
