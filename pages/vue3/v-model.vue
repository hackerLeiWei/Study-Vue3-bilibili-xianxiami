<template>
	<view class="margin-bottom">
		<text class="title">v-model ，支持v-model的组件</text>
	</view>
	<view class="margin-bottom layout-horizontal">
		<input class="padding background-clock" type="text" v-model="inputText" />
		<text class="background-clock" v-on:click="set123">设置内容为 123</text>
	</view>
	<view class="margin-bottom">
		<view class="title" @click="showMsg">点击输出值</view>
	</view>
</template>

<script setup>
	import {
		ref
	} from 'vue'

	const inputText = ref("")

	const set123 = () => {
		inputText.value = 123
		console.log(`set123 inputText:${inputText.value}`)
	}
	const showMsg = () => {
		console.log(`showMsg inputText:${inputText.value}`)
	}
</script>

<style lang="scss" scoped>

</style>
