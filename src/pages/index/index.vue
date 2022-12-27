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
        <uni-grid :showBorder="false" :column="4" @change="change">
          <uni-grid-item class="grid-item" v-for="(item, index) in topic" :index="index" :key="index">
            <view  >
            <view>
              <uni-badge :text="10" :type="error" />
            </view>
           
            <text class="text">{{ item.topicName }}</text>
          </view>
          </uni-grid-item>
        </uni-grid>
      </swiper-item>
    </swiper>
    <uni-grid :showBorder="false" :column="2" @change="change">
      <uni-grid-item class="grid-item-box" v-for="(item, index) in list" :index="index" :key="index">
          <view>
            <text class="text">{{ item.text }}</text>
          </view>
      </uni-grid-item>
    </uni-grid>

    <!--悬浮框--->
    <uni-fab ref="fab" :pattern="pattern" :content="content" :horizontal="horizontal" :vertical="vertical"
      :direction="direction" @trigger="trigger" @fabClick="fabClick"></uni-fab>
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

      horizontal: 'right',
      vertical: 'bottom',
      direction: 'vertical',
      pattern: {
        color: '#cd128f',
        backgroundColor: '#fff',
        selectedColor: '#007AFF',
        buttonColor: '#cd128f',
        iconColor: '#fff',
      },
      content: [{
        iconPath: '/static/local.png',
        selectedIconPath: '/static/local-active.png',
        text: '地区',
        active: false
      },
      {
        iconPath: '/static/add.png',
        selectedIconPath: '/static/add-active.png',
        text: '添加',
        active: false
      },
      {
        iconPath: '/static/message.png',
        selectedIconPath: '/static/message.png',
        text: '消息',
        active: false
      },
      {
        iconPath: '/static/manage.png',
        selectedIconPath: '/static/manage.png',
        text: '设置',
        active: false
      }],

      topics: [[{
        url: "/static/add.png",
        id: "1",
        topicName: "话题1"
      }, {
        url: "/static/add.png",
        id: "2"
        ,
        topicName: "话题2"
      }, {
        url: "/static/add.png",
        id: "3"
        ,
        topicName: "话题3"
      }, {
        url: "/static/add.png", id: "4"
        ,
        topicName: "话题4"
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
      }]
      ],
      //grid
      list: [{
        url: "/static/peng.png",
        text:"怦"
      }, {
        url: "/static/ran.png",
        text:"然"
      }, {
        url: "/static/xin.png",
        text:"心"
      }, {
        url: "/static/dong.png",
        text:"动"
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
    fabClick() {
      uni.showToast({
        title: '点击了悬浮按钮',
        icon: 'none'
      })
    },
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
  width: 90px;
  height: 90px;
  margin-left: 5px;
  margin-top: 5px;
  border-radius: 100px 100px 100px 100px;
  background: rgb(157, 35, 143);
  opacity: 0.5;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}

.grid-item-box {
  width: 180px;
  height: 100%;
  margin-left: 10px;
  margin-top: 8px;
  border-radius: 30px 30px 30px 30px;
  background: rgb(157, 35, 143);
  opacity: 0.5;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}

.text {
  margin-top: 250px;
  margin-left: 25px;
  color: #fff;

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
  height: 200px;
}

.swiper-box1 {
  height: 120px;
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
  background-color: #09bb07;
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

.active {
  border-style: solid;
  border-color: #007aff;
  border-width: 1px;
}
</style>
