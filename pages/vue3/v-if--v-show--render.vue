<template>
	<view class="margin-bottom">
		<view class="title">v-if 条件渲染, 不显示的时候不存在 dom 树中</view>
	</view>
	<view class="margin-bottom">v-show 依然会存在 dom 树中，只是被 display:none 了，如果存在图片，一行会加载请求</view>
	<view class="layout-horizontal background-clock margin-bottom">
		<label>
			<switch @change="onChangedRender" :checked="renderText"></switch>{{renderText?"渲染":"不渲染"}}
		</label>
		<view style="margin:0 20rpx;" v-if="renderText">这个组件渲染了</view>
	</view>
	<view class="layout-vertical background-clock  margin-bottom">
		<view class="margin-bottom">
			v-if，v-else-if v-else</view>
		<view class="margin-bottom" v-if="todayIdxOfWeek===1">星期一</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===2">星期二</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===3">星期三</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===4">星期四</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===5">星期五</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===6">星期六</view>
		<view class="margin-bottom" v-else>星期日</view>
	</view>
	<view class="margin-bottom layout-vertical">
		<view class="margin-bottom">
			v-show 控制的 image 标签，每次进来的时候就会从网络获取图片资源
		</view>
		<label>
			<switch @change="onChangedShowImage" :checked="vShowImage"></switch>{{vShowImage?"v-show":"hiide"}}
		</label>
		<image v-show="vShowImage"
			src="https://img2.baidu.com/it/u=3370757408,2533048260&fm=253&fmt=auto&app=120&f=JPEG?w=1280&h=800"
			mode="aspectFill"></image>
	</view>
	<view class="margin-bottom layout-vertical">
		<view class="margin-bottom">
		</view>
		<label>
			<switch @change="onChangedShowImage" :checked="vShowImage"></switch>{{vShowImage?"v-show":"hiide"}}
		</label>
		<image v-show="vShowImage"
			src="https://picx.zhimg.com/v2-b7d21f25722e8933a8e111e323afb6e8_1440w.jpg?source=172ae18b"
			mode="aspectFill"></image>
	</view>
	<view class="margin-bottom layout-vertical">
		<view class="margin-bottom">
			v-iif 控制的 image 标签，如果不显示，则不会去加载我图片。连 image 标签都被移除了，image 节点被 <!--v-if--> 替代
		</view>

		<label>
			<switch @change="onChangedIfImage" :checked="vIfImage"></switch>{{vIfImage?"v-if: true":"v-if: false。组件元素被移除DOM"}}
		</label>
		<image v-if="vIfImage"
			src="https://picx.zhimg.com/70/c473b8e706c0e486a890bacc22589cdc_1440w.avis?source=172ae18b&biz_tag=Post"
			mode="aspectFill"></image>
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
	const todayIdxOfWeek = ref(0)
	const vShowImage = ref(false)
	const vIfImage = ref(false)

	const onChangedRender = (event) => {
		renderText.value = event.detail.value
		console.log(`${TAG} onChangedRender ${event.detail.value}`)
	}

	const onChangedShowImage = (event) => {
		vShowImage.value = event.detail.value
		console.log(`${TAG} vShowImage ${event.detail.value}`)
	}

	const onChangedIfImage = (event) => {
		vIfImage.value = event.detail.value
		console.log(`${TAG} vIfImage ${event.detail.value}`)
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
		todayIdxOfWeek.value = now.getDay()
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
