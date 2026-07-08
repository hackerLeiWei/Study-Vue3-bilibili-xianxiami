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
			v-if</view>
		<view class="margin-bottom" v-if="todayIdxOfWeek===1">星期一</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===2">星期二</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===3">星期三</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===4">星期四</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===5">星期五</view>
		<view class="margin-bottom" v-else-if="todayIdxOfWeek===6">星期六</view>
		<view class="margin-bottom" v-else>星期天</view>
	</view>
	<view class="margin-bottom layout-vertical">
		<view class="margin-bottom">
			v-show 控制的 image 标签，每次进来的时候就会从网络获取图片资源：https://img2.baidu.com/it/u=3370757408,2533048260&fm=253&fmt=auto&app=120&f=JPEG?w=1280&h=800
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
			v-iif 控制的 image 标签，如果不显示，则不会去加载我图片。连 image 标签都被移除了，用 "removed" 标记，同时节点结尾用 <!--v-if--> 替代
		</view>

		<label>
			<switch @change="onChangedIfImage" :checked="vIfImage"></switch>{{vIfImage?"v-if":"removed"}}
		</label>
		<image v-if="vIfImage"
			src="https://image.baidu.com/search/detail?adpicid=0&b_applid=9997904995296578415&bdtype=0&commodity=&copyright=&cs=1603700319%2C2581383946&di=7646086322926387201&fr=click-pic&fromurl=http%253A%252F%252Fwww.win4000.com%252Fmeinv198437_6.html&gsm=0&hd=&height=0&hot=&ic=&ie=utf-8&imgformat=&imgratio=&imgspn=0&is=0%2C0&isImgSet=&latest=&lid=&lm=&objurl=http%253A%252F%252Fpic1.win4000.com%252Fpic%252F4%252F3e%252Fc125391356.jpg&os=4063581093%2C1083237888&pd=image_content&pi=0&pn=26&rn=1&simid=1603700319%2C2581383946&tn=baiduimagedetail&width=0&word=%E7%BE%8E%E5%A5%B3%E5%9B%BE%E7%89%87%E9%AB%98%E6%B8%85%E5%A3%81%E7%BA%B8&z=&extParams=%7B%22fromPn%22%3A125%2C%22fromCs%22%3A%223417747731%2C2692192528%22%7D"
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
