<template>
  <view class="index-page">
    <!-- paddingTop不生效可换成marginTop -->
    <view class="tab_title" :style="{ paddingTop: statusBarHeight }">
      <uni-row class="demo-uni-row" :gutter="gutter">
					<uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
						<view class="demo-uni-col dark"></view>
					</uni-col>
          <uni-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
             <button class="mini-btn"  style="color:aliceblue; background-color: #cd128f; border-color: #cd128f;   border: 0;"  type="default" size="mini">私会</button>
					</uni-col>
					<uni-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
            <button class="mini-btn" style="  background-color: #cd128f; border-color: #cd128f;   border: 0;" type="default" disabled="true" size="mini">桥头</button>
					</uni-col>
					<uni-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
            <button class="mini-btn" style=" color:aliceblue; background-color: #cd128f; border-color: #cd128f;   border: 0;" type="default" size="mini">银河</button>
					</uni-col>
					<uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
					</uni-col>
				</uni-row>
        <uni-search-bar radius="5" placeholder="搜索" clearButton="always" cancelButton="always" @confirm="search"
				@cancel="cancel" />
        <scroll-view style="height: 80vh;" scroll-y="true" refresher-enabled="true" :refresher-triggered="triggered"
            :refresher-threshold="100" refresher-background="lightgreen" @refresherpulling="onPulling"
            @refresherrefresh="onRefresh" @refresherrestore="onRestore" @refresherabort="onAbort">
        <uni-card title="基础卡片" sub-title="副标题" extra="额外信息" padding="10px 0" :thumbnail="cover">
    
				<image style="width: 100%;" :src="cover"></image>
				<text
					class="uni-body uni-mt-5">卡片组件通用来显示完整独立的一段信息，同时让用户理解他的作用。例如一篇文章的预览图、作者信息、时间等，卡片通常是更复杂和更详细信息的入口点。</text>
				<view slot="actions" class="card-actions">
					<view class="card-actions-item" @click="actionsClick('分享')">
						<uni-icons type="redo" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">分享</text>
					</view>
					<view class="card-actions-item" @click="actionsClick('点赞')">
						<uni-icons type="heart" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">点赞</text>
					</view>
					<view class="card-actions-item" @click="actionsClick('评论')">
						<uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">评论</text>
					</view>
				</view>
			</uni-card>
      <uni-card title="基础卡片" sub-title="副标题" extra="额外信息" padding="10px 0" :thumbnail="cover">
    
    <image style="width: 100%;" :src="cover"></image>
    <text
      class="uni-body uni-mt-5">卡片组件通用来显示完整独立的一段信息，同时让用户理解他的作用。例如一篇文章的预览图、作者信息、时间等，卡片通常是更复杂和更详细信息的入口点。</text>
    <view slot="actions" class="card-actions">
      <view class="card-actions-item" @click="actionsClick('分享')">
        <uni-icons type="redo" size="18" color="#999"></uni-icons>
        <text class="card-actions-item-text">分享</text>
      </view>
      <view class="card-actions-item" @click="actionsClick('点赞')">
        <uni-icons type="heart" size="18" color="#999"></uni-icons>
        <text class="card-actions-item-text">点赞</text>
      </view>
      <view class="card-actions-item" @click="actionsClick('评论')">
        <uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
        <text class="card-actions-item-text">评论</text>
      </view>
    </view>
  </uni-card>
  </scroll-view>
    </view>
   
    </view>
    <view>
  
    
   
    </view>
</template>

<script>
export default {
  name: "main",
  components: {},
  props: {},
  data() {
    return {
      cover: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
      statusBarHeight: uni.getStorageSync('menuInfo').statusBarHeight,//状态栏的高度（可以设置为顶部导航条的padding-top）
      menuWidth: uni.getStorageSync('menuInfo').menuWidth,
      menuHeight: uni.getStorageSync('menuInfo').menuHeight,
      menuBorderRadius: uni.getStorageSync('menuInfo').menuBorderRadius,
      menuRight: uni.getStorageSync('menuInfo').menuRight,
      menuTop: uni.getStorageSync('menuInfo').menuTop,
      contentTop: uni.getStorageSync('menuInfo').contentTop
    }
  },
  computed: {},
  methods: {
    search(res) {
				uni.showToast({
					title: '搜索：' + res.value,
					icon: 'none'
				})
			},
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

<style  scoped>

.uni-card .uni-card__header .uni-card__header-avatar .uni-card__header-avatar-image {
    flex: 1;
    width: 40px;
    height: 40px;
    border-radius: 120px 120px 120px 120px !important;
}
user agent stylesheet

 .left {
      float: left;
      position: absolute;
     
      line-height: 90rpx;
      top: 0;
      bottom: 0;
      left: 20rpx;
      margin: auto;

 }
.box-sizing {
  box-sizing: border-box;
}

.index-page {
  width: 100vw;
  height: calc(100vh - 64px);
}

.tab_title {
  width: 100%;
  height: 44px !important;
  line-height: 44px;
  text-align: center;

  background-color:  #cd128f !important;
  position: fixed;
  top: 0;
  z-index: 9999;
  color: #000;
  font-weight: 500;
}

.menu_btn {
  width: 414rpx !important;

  overflow: hidden;

}

.arrowleft {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-160%, -50%) !important;
  -webkit-transform: translate(-160%, -50%) !important;
}

.text_box {
  width: 1rpx;
  height: 20px;
  background-color: #ddd;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) !important;
  -webkit-transform: translate(-50%, -50%) !important;
}
button::after{
	border: none;
}
.home {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(60%, -50%) !important;
  -webkit-transform: translate(60%, -50%) !important;
}
.demo-uni-row {
		margin-bottom: 10px;


		/* #ifdef MP-TOUTIAO || MP-QQ || MP-BAIDU */
		display: block;
		/* #endif */
	}

	
	/* #ifdef MP-ALIPAY || MP-WEIXIN */
	::v-deep .uni-row {
		margin-bottom: 10px;
	}

	/* #endif */

	.demo-uni-col {
		height: 36px;
		border-radius: 5px;
	}

	.dark_deep {

	}

	.dark {
	
	}

	.light {
		background-color: #e5e9f2;
	}

	.example-body {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 5rpx 10rpx 0;
		overflow: hidden;
	}
  .card-actions {
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
		height: 45px;
		border-top: 1px #eee solid;
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
</style>