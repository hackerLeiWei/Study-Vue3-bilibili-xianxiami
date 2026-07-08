<template>
	<view class="margin-bottom">
		<view class="title">v-on: <==> @</view>
	</view>

	<view class="margin-bottom">
		<view class="title">v-on:事件 <==> @事件</view>
	</view>

	<view class="box" v-on:click="clickNumber">
		<text v-bind:style="{fontSize:fontSize+'rpx',backgroundColor:bgColor,color:textColor}">点击了 {{number}} 次</text>
	</view>
	<view style="margin-top: 50rpx;">
		<switch v-on:change="onSwitchChanged" :checked=!isLoading> </switch>是否同意协议
	</view>
	<button style="margin-top: 20rpx;" type="primary" :loading="isLoading">登录</button>
</template>

<script setup>
	import {
		ref,
		computed
	} from 'vue'

	const TAG = "v-on.vue"
	const number = ref(0)
	const fontSize = ref(30)
	const bgColor = ref('#f0f0f0')
	const isLoading = ref(true)

	const clickNumber = () => {
		number.value++
		if (fontSize.value < 60) {
			fontSize.value += 3
		}
		bgColor.value = `#${String(Math.random()).substring(2, 8)}`
	}

	const textColor = computed(() => {
		// 1. 将十六进制转为 RGB
		const hex = bgColor.value.replace('#', '')
		const r = parseInt(hex.substring(0, 2), 16)
		const g = parseInt(hex.substring(2, 4), 16)
		const b = parseInt(hex.substring(4, 6), 16)

		// 2. 计算亮度公式 (人眼感光权重)
		const luminance = (r * 299 + g * 587 + b * 114) / 1000

		// 3. 亮度大于 128 用黑色，否则用白色
		return luminance > 128 ? '#000000' : '#FFFFFF'
	})

	const onSwitchChanged = (event) => {
		isLoading.value = !event.detail.value
		console.log(`${TAG} ${isLoading.value}`)
	}
</script>

<style lang="scss" scoped>
	.box {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 80vw;
		height: 100rpx;
		background: orange;
	}
</style>