<template>
   <view class="container">
    <scroll-view style="height: 100vh;" scroll-y="true" refresher-enabled="true" :refresher-triggered="triggered"
      :refresher-threshold="100" refresher-background="lightgreen" @refresherpulling="onPulling"
      @refresherrefresh="onRefresh" @refresherrestore="onRestore" @refresherabort="onAbort">

      <uni-card title="青菜紫罗冬瓜" sub-title="18岁*广州*本科*市场营销" extra="***" :thumbnail="avatar" @click="onClick">
        <template v-slot:title>
          <uni-row class="demo-uni-row" :gutter="gutter" :width="nvueWidth">
            <uni-col :span="3">
              <image style="  border-radius: 120px 120px 120px 120px; height: 40px; width: 40px; margin-top: 10px;"
                :src="avatar"></image>
            </uni-col>
            <uni-col :span="18">
              <uni-row :gutter="gutter" :width="nvueWidth">
                <view style="margin-top: 15px;">
                  <text class="card-text">青菜紫罗冬瓜</text>
                </view>
              </uni-row>
              <uni-row :gutter="gutter" :width="nvueWidth">
                <view style="margin-top: -8px;">
                  <text class="card-text1">18岁*广州*本科*市场营销</text>
                </view>
              </uni-row>
            </uni-col>
            <uni-col :span="3">
              <view class="mini-btn" @click="actionsClick('弹层', 1, 2)"
                style="margin-top: 10px; background-color: white; border-color: #cd128f;border: 0;" type="default"
                size="mini">...</view >
            </uni-col>
          </uni-row>
        </template>
        <image style="width: 100%;" :src="cover"></image>
        <text class="uni-body uni-mt-5">而立之年不啻过，十分减尽少年豪。吃它官饭如何稳，着了朝衫说甚高。
勤向溪山供日课，剩栽花木足年劳。客来不周嗟无肉，菜本新添数百窠。</text>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('分享')">
            <uni-icons type="redo" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">分享(1314)</text>
          </view>
          <view class="card-actions-item" @click="actionsClick('点赞')">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">点赞(520)</text>
          </view>
          <view class="card-actions-item" @click="actionsClick('评论')">
            <uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">评论(888)</text>
          </view>
        </view>
      </uni-card>
      <uni-card title="青菜紫罗冬瓜" sub-title="18岁*广州*本科*市场营销" extra="***" :thumbnail="avatar" @click="onClick">
        <template v-slot:title>
          <uni-row class="demo-uni-row" :gutter="gutter" :width="nvueWidth">
            <uni-col :span="3">
              <image style="  border-radius: 120px 120px 120px 120px; height: 40px; width: 40px; margin-top: 10px;"
                :src="avatar"></image>
            </uni-col>
            <uni-col :span="18">
              <uni-row :gutter="gutter" :width="nvueWidth">
                <view style="margin-top: 15px;">
                  <text class="card-text">青菜紫罗冬瓜</text>
                </view>
              </uni-row>
              <uni-row :gutter="gutter" :width="nvueWidth">
                <view style="margin-top: -8px;">
                  <text class="card-text1">18岁*广州*本科*市场营销</text>
                </view>
              </uni-row>
            </uni-col>
            <uni-col :span="3">
              <view  class="mini-btn" @click="actionsClick('弹层', 1, 2)"
                style="margin-top: 10px; background-color: white; border-color: #cd128f;border: 0;" type="default"
                size="mini">...</view >
            </uni-col>
          </uni-row>
        </template>
        <image style="width: 100%;" :src="cover"></image>
        <text class="uni-body uni-mt-5">而立之年不啻过，十分减尽少年豪。吃它官饭如何稳，着了朝衫说甚高。
勤向溪山供日课，剩栽花木足年劳。客来不周嗟无肉，菜本新添数百窠。</text>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('分享')">
            <uni-icons type="redo" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">分享(1314)</text>
          </view>
          <view class="card-actions-item" @click="actionsClick('点赞')">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">点赞(520)</text>
          </view>
          <view class="card-actions-item" @click="actionsClick('评论')">
            <uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">评论(888)</text>
          </view>
        </view>
      </uni-card>
      </scroll-view>
   </view>
</template>

<script>
export default {
  name: "dynamic",
  components: {},
  props: {},
  data() {
    return {
      cover: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
      avatar: 'https://flipped.lncios.cn/queqiao-active.png'
    }
  },
  computed: {},
  methods: {
    actionsClick(val, val1, val2) {
      switch (val) {
        case '弹层':
          uni.showToast({
            title: '点击了弹层按钮',
            icon: 'none'
          })
          this.$refs.popup.open("bottom")
          break;
        case '点赞':
          uni.showToast({
            title: '点击了点赞按钮',
            icon: 'none'
          })
          break;
        case '分享':
          uni.showToast({
            title: '点击了分享按钮',
            icon: 'none'
          })
          this.$refs.share.open("bottom")
          break;
        case '评论':
          uni.showToast({
            title: '点击了评论按钮',
            icon: 'none'
          })
          break;

      }
    }
  },
  watch: {},

  // 页面周期函数--监听页面加载
  onLoad() {},
  // 页面周期函数--监听页面初次渲染完成
  onReady() {},
  // 页面周期函数--监听页面显示(not-nvue)
  onShow() {},
  // 页面周期函数--监听页面隐藏
  onHide() {},
  // 页面周期函数--监听页面卸载
  onUnload() {},
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

.text-style {
  position: absolute;
  top: 220upx;
  left: 20upx;
  font-size: 35upx;
  color: #FFFFFF;
}
.text-style1{
  position: absolute;
  top: 270upx;
  left: 39%;
  background-color: rgb(211, 234, 9);
  border-radius: 50px 50px 50px 50px;
}
.image-radius {
  width: 100%;
  height: 100%;
  z-index: -100;
  filter: progid:DXImageTransform.Microsoft.alpha(opacity=50);
}
.demo-uni-row {
  margin-bottom: 10px;


  /* #ifdef MP-TOUTIAO || MP-QQ || MP-BAIDU */
  display: block;
  /* #endif */
}
.card-actions-item {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.card-actions-item-text {
  font-size: 12px;
  color: #666;
  margin-left: 5px;
}

.card-text {
  font-size: 15px;
  font-style: normal;


}
.card-actions {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  height: 45px;
  border-top: 1px #eee solid;
}
.card-text1 {
  font-size: 10px;
  margin-top: 30px;
  font-style: normal;
}
.card-text {
  font-size: 15px;
  font-style: normal;


}
</style>