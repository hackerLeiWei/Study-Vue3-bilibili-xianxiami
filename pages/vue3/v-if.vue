<template>
	<view class="margin-bottom">
		<view class="title">v-if 条件渲染, 不显示的时候不存在 dom 树中</view>
	</view>
	<view class="margin-bottom">v-show 依然会存在 dom 树中，只是被 display:none 了，如果存在图片，一行会加载请求</view>
	<view class="layout-horizontal background-clock margin-bottom">
		<label>
			<switch @change="onChanged" :checked="renderText"></switch>{{renderText?"渲染":"不渲染"}}
		</label>
		<view style="margin:0 20rpx;" v-if="renderText">这个组件渲染了</view>
	</view>
	<view class="layout-vertical background-clock  margin-bottom">
		<view class="margin-bottom">
			v-if</view>
		<view class="margin-bottom" v-if="today===1">星期一</view>
		<view class="margin-bottom" v-else-if="today===2">星期一</view>
		<view class="margin-bottom" v-else-if="today===3">星期二</view>
		<view class="margin-bottom" v-else-if="today===4">星期三</view>
		<view class="margin-bottom" v-else-if="today===5">星期四</view>
		<view class="margin-bottom" v-else-if="today===6">星期五</view>
		<view class="margin-bottom" v-else>星期天</view>
	</view>
</template>

<script setup>
	import {
		ref,
		onMounted
	} from 'vue'

	const TAG = "v-if.vue"
	const renderText = ref(true)
	const currentTime = ref('')
	const today = ref(0)

	console.log(`${TAG} today:${today.value}`)

	const onChanged = (event) => {
		renderText.value = event.detail.value
		console.log(`${TAG} onChanged ${event.detail.value}`)
	}

	const updateTime = () => {
		const now = new Date()
		const y = now.getFullYear()
		const m = String(now.getMonth() + 1).padStart(2, '0')
		const d = String(now.getDate()).padStart(2, '0')
		const h = String(now.getHours()).padStart(2, '0')
		const min = String(now.getMinutes()).padStart(2, '0')
		const s = String(now.getSeconds()).padStart(2, '0')
		const week = ['日', '一', '二', '三', '四', '五', '六'][now.getDay()]
		today.value = now.getDay()
		currentTime.value = `${y}-${m}-${d} ${h}:${min}:${s} 星期${week}`
		console.log(`${TAG} currentTime:${currentTime.value}`)
	}

	onMounted(() => {
		updateTime()
		// 若需要实时更新，可开启定时器（注意清除）
	})
</script>

<style lang="scss" scoped>

</style>