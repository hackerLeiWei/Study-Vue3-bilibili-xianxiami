<template>
	<view class="margin-bottom">
		<text class="title">v-bind: <==> :</text>
	</view>
	<view class="margin-bottom">
		<text>v-bind:属性 <==> :属性</text>
		<text>v-bind:属性 是单向绑定。它只会将ref变量变动的值“推”到组件，但组件改变时不会“拉”回数据，ref变量的值不会跟随变</text>
	</view>

	<view class="margin-bottom">
		<text>v-bind:class <==> :class</text>
	</view>

	<view class="margin-bottom">
		<!-- 存在多个 class 时，后面的会覆盖前面的
		<view class="box activite">
		<view class="box" v-bind:class="'activite'">
		<view class="box" v-bind:class="{activite:true}">
		<view class="box" v-bind:class="{activite:isActive}">
		<view class="box" v-bind:class="isActive?'activite':''">
		-->
		<view class="box" v-bind:class="isActive?'activite':''">
			v-bind:class 动态改变 class
		</view>
		<view class="box" style="white-space: pre-wrap;">
			{{`<view class="box activite">\n<view class="box" v-bind:class="'activite'">\n<view class="box" v-bind:class="{activite:true}">\n<view class="box" v-bind:class="{activite:isActive}">\n<view class="box" v-bind:class="isActive?'activite':''">`}}
		</view>
	</view>

	<view class="margin-bottom">
		<view class="box" v-bind:class="isActive?'activite':''">
			v-bind:style 动态改变 style
		</view>
		<view class="box" v-bind:style="{width: 80+'vw', fontSize: fontSize+'rpx'}">
			v-bind:style 内联样式
		</view>
	</view>

	<view class="margin-bottom">
		<image style="width: 100vw; height: 300rpx;" v-bind:src="picUrl1[index]" mode="aspectFill">
		</image>
	</view>
	<view class="margin-bottom"><button type="primary"
			v-bind:loading="isLoading">{{isLoading?"正在加载中...":"加载完成"}}</button></view>


</template>

<script setup>
	import {
		ref,
		onMounted
	} from 'vue';
	import {
		onLoad,
		onUnload,
		onReady,
		onShow,
		onHide
	} from '@dcloudio/uni-app'

	const TAG = "v-x.vue"

	const isLoading = ref(true)

	const index = ref(0)
	const picUrl1 = ["/static/swiper-items/swiper-item-01.webp", "/static/swiper-items/swiper-item-02.webp",
		"/static/swiper-items/swiper-item-03.webp",
		"/static/swiper-items/swiper-item-04.webp"
	];
	let times = 0
	let timmer = null
	const isActive = ref(false)
	const fontSize = ref(30)

	// ------------------------------------lifecycle start
	onMounted(() => {
		console.log(`${TAG} 页面 onMounted`)
	})
	onLoad((options) => {
		console.log(`${TAG} 页面 onLoad options:${options}`)
		timmer = setInterval(() => {
			times++
			index.value = times % picUrl1.length
			if (times === 5) {
				isLoading.value = false
			}
			fontSize.value = 30 + (times % 4) * 10
			isActive.value = index.value % 2 === 1
			console.log(`${TAG} times；${times}`)
		}, 2000)
	})
	onShow(() => {
		console.log(`${TAG} 页面 onShow`)
	})
	onHide(() => {
		console.log(`${TAG} 页面 onHide`)
	})
	onUnload(() => {
		console.log(`${TAG} 页面 onUnload`)
		if (timmer) {
			clearInterval(timmer)
			timmer = null
		}
	})
	// ------------------------------------lifecycle end
</script>

<style lang="scss" scoped> // scoped 仅限当前组件使用，不会污染到其他组件
	.box {
		width: 100vw;
		background: orange;
	}

	.activite {
		background: green;
		color: white;
	}
</style>
