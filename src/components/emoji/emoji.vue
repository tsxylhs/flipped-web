<template>
    <view class="emoji" :style="{ height: height + 'px' }">
        <view class="emoji-line" v-for="(line, i) in emoji" :key="i">
            <view class="emoji-line-item" v-for="(item, index) in line" :key="index" @tap="clickEmoji(item)">{{ item }}
            </view>
        </view>
    </view>
</template>

<script>
export default {
    props: {
        height: {
            type: Number,
            default: 160
        }
    },
    name: "emoji",
    data() {
        return {
            emoji: [[
                "eee", "😀", "😀"
            ]]

        }
    }
}
</script>
            