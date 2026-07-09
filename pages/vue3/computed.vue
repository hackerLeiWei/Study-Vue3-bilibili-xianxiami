<template>

	<view class="title">
		计算属性
	</view>
	<view class="margin-bottom">
		<input type="text" class="input" v-model="inputLastName" placeholder="Last name:" />
	</view>
	<view class="margin-bottom">
		<input type="text" class="input" v-model="inputFirstName" placeholder="First name:" />
	</view>
	<view class="background-clock layout-vertical">
		<text>计算属性，有缓存</text>
		<text>{{fullName}}</text>
		<text>{{fullName}}</text>
		<text>{{fullName}}</text>
	</view>
	<view class="background-clock layout-vertical">
		<text>方法执行，无缓存</text>
		<text>{{fullName2()}}</text>
		<text>{{fullName2()}}</text>
		<text>{{fullName2()}}</text>
	</view>

</template>

<script setup>
	import {
		computed,
		ref
	} from 'vue'

	const inputLastName = ref("你好")
	const inputFirstName = ref("哈哈")

	/**
	 * 计算属性，会缓存，无需 () 使用。不宜改动，可当作 ref() 属性，输出结果类似
	 */
	// const fullName = computed(() => "全称：" + inputLastName.value + "·" + inputFirstName.value)
	const fullName = computed(() => {
		console.log("计算属性执行")
		return "全称：" + inputLastName.value + "·" + inputFirstName.value
	})

	console.log(fullName)
	/**
	 * 方法，每次调用都需要运行，没有缓存，需要带 ()使用
	 */
	// const fullName2 = () => "全称：" + inputLastName.value + "·" + inputFirstName.value
	const fullName2 = () => {
		console.log("方法执行")
		return "全称：" + inputLastName.value + "·" + inputFirstName.value
	}


</script>

<style lang="scss" scoped>
	.input {
		width: 100vw;
		height: 60rpx;
		padding: 0 20rpx;
		border: 1rpx solid #f0f0f0;
	}
</style>
