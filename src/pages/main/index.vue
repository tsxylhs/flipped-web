<template>
  <view class="index-page">
    <!-- paddingTop不生效可换成marginTop -->
    <view class="tab_title" :style="{ paddingTop: statusBarHeight }">
      <uni-row class="demo-uni-row" :gutter="gutter">
        <uni-col :xs="6" :sm="3" :md="4" :lg="3" :xl="1">
          <view class="demo-uni-col dark"></view>
        </uni-col>
        <uni-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
          <view :style="typeStyleActive1" type="default" @click="changeTips(1)">私会</view>
        </uni-col>
        <uni-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
          <view :style="typeStyleActive2" disabled="true" @click="changeTips(2)">桥头</view>
        </uni-col>
        <uni-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
          <view :style="typeStyleActive3" type="default" @click="changeTips(3)" size="mini">银河</view>
        </uni-col>
        <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
          <view class="demo-uni-col dark"></view>
        </uni-col>
      </uni-row>

      <uni-fab v-if="active==2" ref="fab" :pattern="pattern" :content="content" :horizontal="horizontal" :vertical="vertical"
        :direction="direction" @trigger="trigger" @fabClick="fabClick"></uni-fab>
      <view>
        <!-- 普通弹窗 -->
        <uni-popup ref="popup" safe-area="false" background-color="#fff" type="bottom" @change="change">
          <button style="margin-top: 3px; background-color: white; font-size: 15px;"> 关注</button>
          <button style="margin-top: 3px;background-color: white; font-size: 15px;"> 不看他（她）</button>
          <button style="margin-top: 3px;background-color: white; font-size: 15px;"> 举报</button>
          <button style="margin-top: 10px;background-color: white; font-size: 15px; "> 取消</button>
        </uni-popup>
        <uni-popup ref="share" background-color="#fff" type="bottom" @change="change">
          <uni-popup-share></uni-popup-share>
        </uni-popup>
      </view>
    </view>
  </view>

  <!-- 私会 -->
  <view v-if="active == 1" style="height:80vh" >
   <focus></focus>
  </view>
  <!-- 桥头 -->
  <view v-if="active == 2" class="container">
    <uni-search-bar style="margin-top: 10px;" radius="5" placeholder="搜索" clearButton="always" cancelButton="always"
      @confirm="search" @cancel="cancel" />
    <scroll-view style="height: 80vh;" scroll-y="true" refresher-enabled="true" :refresher-triggered="triggered"
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
                <view style="margin-top: -12px;">
                  <text class="card-text1">18岁*广州*本科*市场营销</text>
                </view>
              </uni-row>
            </uni-col>
            <uni-col :span="3">
              <button class="mini-btn" @click="actionsClick('弹层', 1, 2)"
                style="margin-top: 10px; background-color: white; border-color: #cd128f;border: 0;" type="default"
                size="mini">...</button>
            </uni-col>
          </uni-row>
        </template>
        <image style="width: 100%;" :src="cover"></image>
        <text class="uni-body uni-mt-5">卡片组件通用来显示完整独立的一段信息，同时让用户理解他的作用。例如一篇文章的预览图、作者信息、时间等，卡片通常是更复杂和更详细信息的入口点。</text>
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
                <view style="margin-top: -12px;">
                  <text class="card-text1">18岁*广州*本科*市场营销</text>
                </view>
              </uni-row>
            </uni-col>
            <uni-col :span="3">
              <button class="mini-btn" @click="actionsClick('弹层', 1, 2)"
                style="margin-top: 10px; background-color: white; border-color: #cd128f;border: 0;" type="default"
                size="mini">...</button>
            </uni-col>
          </uni-row>
        </template>
        <image style="width: 100%;" :src="cover"></image>
        <text class="uni-body uni-mt-5">卡片组件通用来显示完整独立的一段信息，同时让用户理解他的作用。例如一篇文章的预览图、作者信息、时间等，卡片通常是更复杂和更详细信息的入口点。</text>
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

      <uni-card title="基础卡片" sub-title="副标题" extra="额外信息" :thumbnail="avatar" @click="onClick">
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
                <view style="margin-top: -12px;">
                  <text class="card-text1">18岁*广州*本科*市场营销</text>
                </view>
              </uni-row>
            </uni-col>
            <uni-col :span="3">
              <button class="mini-btn" @click="actionsClick('弹层', 1, 2)"
                style="margin-top: 10px; background-color: white; border-color: #cd128f;border: 0;" type="default"
                size="mini">...</button>
            </uni-col>
          </uni-row>
        </template>
        <image style="width: 100%;" :src="cover"></image>
        <text class="uni-body">这是一个带头像和双标题的基础卡片，此示例展示了一个完整的卡片。</text>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('分享', 1, 2)">
            <uni-icons type="redo" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">分享</text>
          </view>
          <view class="card-actions-item" @click="actionsClick('点赞', 1, 2)">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">点赞</text>
          </view>
          <view class="card-actions-item" @click="actionsClick('评论', 1, 2)">
            <uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
            <text class="card-actions-item-text">评论</text>
          </view>
        </view>
      </uni-card>
    </scroll-view>
  </view>
  <!--聊天 -->
  <view v-if="active == 3" style="height:80vh">
    <chatIndex></chatIndex>
	</view>






</template>

<script>
	import focus from '../../components/focus/index.vue'
	import chatIndex from '../../components/chatIndex/index.vue'
  const innerAudioContext = uni.createInnerAudioContext();
export default {
  name: "main",
  components: { chatIndex,focus},
  props: {},
  data() {
    return {
      ///333
      

      inputValue:"",
      //1111
      list: [{
        id:"1",
        name:"小花",
        count:"2",
        text:"这里有个姑娘叫小花",
        url: 'https://flipped.lncios.cn/queqiao.png'
      }, {
        id:"2",
        name:"萝卜",
        count:"4",
        text:"这里有个姑娘叫小花",
        url: 'https://flipped.lncios.cn/queqiao-active.png'
      }, {
        id:"3",
        name:"青菜",
        count:"1",
        text:"这里有个姑娘叫小花",
        url: 'https://flipped.lncios.cn/xiaoyuan.jpg'
      }],

    
    




      // 2222
      active: 2,
      typeStyleActive1: {},
      typeStyleActive2: {},
      typeStyleActive3: {},
      //样式
      typeStyle: {
        color: "aliceblue",
        backgroundColor: "#cd128f",
        borderRadius: "220px 220px 220px 220px",
        borderColor: "#cd128f",
      },
      typeStyleActive: {
        color: "aliceblue",
        backgroundColor: "#cd128f",
        borderRadius: "220px 220px 220px 220px",
        borderColor: "#7A90F9",
        color: " #007aff",
        marginTop: "8px",


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
      cover: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/094a9dc0-50c0-11eb-b680-7980c8a877b8.jpg',
      avatar: 'https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png',
      statusBarHeight: uni.getStorageSync('menuInfo').statusBarHeight,//状态栏的高度（可以设置为顶部导航条的padding-top）
      menuWidth: uni.getStorageSync('menuInfo').menuWidth,
      menuHeight: uni.getStorageSync('menuInfo').menuHeight,
      menuBorderRadius: uni.getStorageSync('menuInfo').menuBorderRadius,
      menuRight: uni.getStorageSync('menuInfo').menuRight,
      menuTop: uni.getStorageSync('menuInfo').menuTop,
      contentTop: uni.getStorageSync('menuInfo').contentTop,
      content: [{
        iconPath: 'https://flipped.lncios.cn/local.png',
        selectedIconPath: 'https://flipped.lncios.cn/local-active.png',
        text: '地区',
        active: false
      },
      {
        iconPath: 'https://flipped.lncios.cn/add.png',
        selectedIconPath: 'https://flipped.lncios.cn/add-active.png',
        text: '添加',
        active: false
      },
      {
        iconPath: 'https://flipped.lncios.cn/message.png',
        selectedIconPath: 'https://flipped.lncios.cn/message.png',
        text: '消息',
        active: false
      },
      {
        iconPath: 'https://flipped.lncios.cn/manage.png',
        selectedIconPath: 'https://flipped.lncios.cn/manage.png',
        text: '设置',
        active: false
      }]
    }
  },
  computed: {},
  methods: {

    ///3333
   

      //222
    changeTips(type) {
      switch (type) {
        case 1:
          this.typeStyleActive2 = this.typeStyle;
          this.typeStyleActive1 = this.typeStyleActive;
          this.typeStyleActive3 = this.typeStyle;
          this.active = 1;
          break;
        case 2:
          this.typeStyleActive1 = this.typeStyle;
          this.typeStyleActive2 = this.typeStyleActive;
          this.typeStyleActive3 = this.typeStyle;
          this.active = 2;
          break;
        case 3:
          this.typeStyleActive2 = this.typeStyle;
          this.typeStyleActive3 = this.typeStyleActive;
          this.typeStyleActive1 = this.typeStyle;
          this.active = 3;
          break;
      }
    },
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
    },
    fabClick() {
      uni.showToast({
        title: '点击了悬浮按钮',
        icon: 'none'
      })
    },
    search(res) {
      uni.showToast({
        title: '搜索：' + res.value,
        icon: 'none'
      })
    },
  },
  watch: {},

  // 页面周期函数--监听页面加载
  onLoad() {
    this.typeStyleActive1 = this.typeStyle;
    this.typeStyleActive2 = this.typeStyleActive;
    this.typeStyleActive3 = this.typeStyle;
  },
  // 页面周期函数--监听页面初次渲染完成
  onReady() { },
  // 页面周期函数--监听页面显示(not-nvue)
  onShow() {
			// 数组倒叙 主要是应对后端传过来的数据

		},
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

<style  lang="scss">
.chat-custom-right {
  flex: 1;
  /* #ifndef APP-NVUE */
  display: flex;
  /* #endif */
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-end;
}

.chat-custom-text {
  font-size: 12px;
  color: #999;
}


.index-page {
  width: 100vw;
  height: 12vh;
}

.tab_title {
  width: 100%;
  height: 44px !important;
  line-height: 44px;
  text-align: center;

  background-color: #cd128f !important;
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

button::after {
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

.dark_deep {}

.dark {}

.light {
  background-color: #1f9deb;
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

.card-text {
  font-size: 15px;
  font-style: normal;


}

.card-text1 {
  font-size: 10px;
  font-style: normal;
}





</style>