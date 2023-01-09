<template>
  <view class="container">
    <view style="height: 27vh; background-image: linear-gradient(to bottom, #cd128f, #DcDCdc);">
      <uni-row class="demo-uni-row" :gutter="gutter" :width="nvueWidth">
        <uni-col :span="3">
          <cover-image
            style="  border-radius: 120px 120px 120px 120px; height: 40px; width: 40px; margin-top: 10px; margin-left: 20px;"
            :src="avatar"></cover-image>
        </uni-col>
        <uni-col :span="17">
          <uni-row :gutter="gutter" :width="nvueWidth">
            <view style="margin-top: 15px;  margin-left: 20px">
              <text class="card-text">青菜紫罗冬瓜</text>
            </view>
          </uni-row>
          <uni-row :gutter="gutter" :width="nvueWidth">
            <view style="margin-top: -10px;  margin-left: 20px">
              <text class="card-text1">个性签名</text>
            </view>
          </uni-row>
        </uni-col>
        <!-- <button type="default"
          style="margin-top: 20px; color: white; background-color: transparent; border: 0px; opacity: 0.8;font: 0.2em sans-serif;">编辑</button> -->
      </uni-row>
      <view>
        <uni-grid :column="4" :highlight="false" @change="change" :showBorder="false" :square="false">
          <uni-grid-item v-for="(item, index) in list" :index="index" :key="index">
            <view style="background-color: transparent;  " >
              <uni-row :gutter="gutter" :width="nvueWidth">
                <image style="margin-left: 35%; margin-top: 20%; height: 40px;width: 40px;" :src="item.url">
                </image>
              </uni-row>
              <uni-row :gutter="gutter" :width="nvueWidth">
                <text style="text-align:center; margin-left: 30%; color:white; font-size: 12px;">{{ item.text }}</text>
              </uni-row>
            </view>
          </uni-grid-item>
        </uni-grid>
      </view>

    </view>

    <view style="height: 15vh; margin-top: 3px; ">
      <uni-section title="常用功能" type="line" padding>
        <uni-grid :showBorder="false" :column="3" :square="true" :highlight="false" @change="change">
          <uni-grid-item v-for="(item, index) in list1" :index="index" :key="index">
            <view class="grid-item-box" @click="choose(item)">
              <image style="height: 40px; width: 40px;" :src="item.url"></image>
              <text class="textm">{{ item.text }}</text>
            </view>
          </uni-grid-item>
        </uni-grid>
      </uni-section>

    </view>
  </view>
</template>

<script>
export default {
  name: "me",
  components: {},
  props: {},
  data() {
    return {
      cover: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
      avatar: 'https://flipped.lncios.cn/queqiao-active.png',
      list: [{
        url: "https://flipped.lncios.cn/guanzhu1.png",
        text: "舔狗(100)"
      }, {
        url: "https://flipped.lncios.cn/guanzhu.png",
        text: "倾心(12)"
      }, {
        url: "https://flipped.lncios.cn/laifang.png",
        text: "来访(+10)"
      }, {
        url: "/static/zan.png",
        text: "点赞(+120)"
      }],
      list1: [{
        id: "1",
        url: 'https://flipped.lncios.cn/shiming.png',
        text: '实名认证',
        badge: '0',
        type: "primary"
      },
      {
        id: "1",
        url: 'https://flipped.lncios.cn/dongtai.png',
        text: '我的动态',
        badge: '1',
        type: "success"
      },
      {
        id: "1",
        url: 'https://flipped.lncios.cn/wanshan.png',
        text: '信息完善',
        badge: '1',
        type: "success"
      },
      {
        id: "1",
        url: 'https://flipped.lncios.cn/gongzhonghao.png',
        text: '公众号',
        badge: '99',
        type: "warning"
      },
      {
        id: "1",
        url: 'https://flipped.lncios.cn/huodong.png',
        text: '活动报名'
      },
      {
        id: "1",
        url: 'https://flipped.lncios.cn/yingyong.png',
        text: '应用声明'
      },
      {
        url: 'https://flipped.lncios.cn/fuwu.png',
        text: '服务与帮助'
      },
      {
        id: "1",
        url: 'https://flipped.lncios.cn/shezhi.png',
        text: '设置',
        badge: '2',
        type: "error"
      }

      ]
    }
  },
  computed: {},
  methods: {
    choose(item) {
      console.log(item.id);
      switch (item.id) {
        case "1":
          uni.navigateTo({
            url: "/pages/actives/index?type=1",
            animationType: 'fade-in',
            animationDuration: 200
          })
          break;
      }
    }
  },
  watch: {},

  // 页面周期函数--监听页面加载
  onLoad() { },
  // 页面周期函数--监听页面初次渲染完成
  onReady() { },
  // 页面周期函数--监听页面显示(not-nvue)
  onShow() { },
  // 页面周期函数--监听页面隐藏
  onHide() { },
  // 页面周期函数--监听页面卸载
  onUnload() { },
  // 页面处理函数--监听用户下拉动作
  // onPullDownRefresh() { uni.stopPullDownRefresh(); },
  // 页面处理函数--监听用户上拉触底
  // onReachBottom() {},
  // 页面处理函数--监听页面滚动(not-nvue)
  // onPageScroll(event) {},
  // 页面处理函数--用户点击右上角分享
  // onShareAppMessage(options) {},
} 
</script>

<style scoped>
.card-text {
  font-size: 15px;
  font-style: normal;
  color: white;


}

.demo-uni-row {
  margin-bottom: 10px;
  width: 130rpx;
  background-color: aliceblue;
  /* #ifdef MP-TOUTIAO || MP-QQ || MP-BAIDU */
  display: block;
  /* #endif */
}

.demo-uni-col {
  height: 36px;
  border-radius: 5px;
}

.dark_deep {
  background-color: #99a9bf;
}

.card-text1 {
  font-size: 10px;
  color: white;

  font-style: normal;
}

.grid-item-box {
  flex: 1;

  /* #ifndef APP-NVUE */
  display: flex;
  /* #endif */
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 10px;
  margin-left: 2px;
  margin-top: 2px;
  border-radius: 30px 30px 30px 30px;
  background-image: linear-gradient(to bottom, #dc5cb1, #e28d8d);
}

.textm {
  margin-top: 4px;
  color: aliceblue;
}
</style>