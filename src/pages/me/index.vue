<template>
  <view class="container">
    <view style="height: 30vh; background-image: linear-gradient(to bottom, #cd128f, #DcDCdc);;">
      <uni-row class="demo-uni-row" :gutter="gutter" :width="nvueWidth">
        <uni-col :span="3">
          <cover-image
            style="  border-radius: 120px 120px 120px 120px; height: 40px; width: 40px; margin-top: 10px; margin-left: 20px; margin-top: 10px;"
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
        <button type="default"
          style="margin-top: 20px; color: white; background-color: transparent; border: 0; opacity: 0.8;font: 0.1em sans-serif;">编辑</button>
      </uni-row>
      <view style="margin-top: 35px;">
        <uni-grid :column="4" :highlight="true" @change="change" :showBorder="false" highlight="false" :square="false">
          <uni-grid-item v-for="(item, index) in list" :index="index" :key="index" >
            <view class="grid-item-box" style="background-color: transparent;  ">
              <uni-row :gutter="gutter" :width="nvueWidth">
              <image style="margin-left: 35%; margin-top: 20%; height: 40px;width: 40px;" :src="item.url"></image>
              </uni-row>
              <uni-row :gutter="gutter" :width="nvueWidth">
              <text style="text-align:center; margin-left: 34%; color:white; font-size: 12px;">{{item.text}}</text>
            </uni-row>
            </view>
          </uni-grid-item>
        </uni-grid>
      </view>

    </view>

    <view style="height: 15vh; ">
     
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
      avatar: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png',
      list: [{
        url: "/static/guanzhu1.png",
        text: "我的关注"
      }, {
        url: "/static/guanzhu.png",
        text: "关注我的"
      }, {
        url: "/static/laifang.png",
        text: "最近来访"
      }, {
        url: "/static/wanshan.png",
        text: "完善信息"
      }]
    }
  },
  computed: {},
  methods: {},
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
</style>