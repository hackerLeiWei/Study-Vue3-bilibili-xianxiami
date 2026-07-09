<template>
	<view class="margin-bottom">
		<text class="title">侦听器 watch</text>
	</view>
	<view class="margin-bottom background-clock">
		<text>watch 可以获取网络数据监听，计算属性无法做到 https://cn.vuejs.org/guide/essentials/watchers.html</text>
	</view>
	<view class="margin-bottom background-clock">
		<text>
			在 setup() 或 script setup中用同步语句创建的侦听器，会自动绑定到宿主组件实例上，并且会在宿主组件卸载时自动停止。因此，在大多数情况下，你无需关心怎么停止一个侦听器。一个关键点是，侦听器必须用同步语句创建：如果用异步回调创建一个侦听器，那么它不会绑定到当前组件上，你必须手动停止它，以防内存泄漏
		</text>
	</view>

	<view class="layout-vertical margin-bottom">
		<text>输入inputText：</text>
		<input class="border-input" type="text" placeholder="请输入内容：" v-model="inputText" />
	</view>
	<view class="layout-vertical margin-bottom">
		<text>输入名字：</text>
		<input class="border-input" type="text" placeholder="" v-model="person.name" />
		<text>{{person}}</text>
	</view>

</template>

<script setup>
	import {
		ref,
		watch,
		watchEffect
	} from 'vue'

	const inputText = ref("")
	const person = ref({
		name: "",
		age: 20
	})

	watch(inputText, (newValue, oldValue) => {
		console.log(`newValue:${newValue}  oldValue:${oldValue}`)
	})

	watch(inputText, (newValue) => {
		console.log(`newValue:${newValue}`)
	})

	/**
	 * 下面操作无法侦听到对象中的字段变更，是一种浅层侦听
	 */
	watch(person, (newValue) => {
		console.log("person")
		console.log(newValue)
	})

	/**
	 * 开启对象深度侦听
	 */
	watch(person, (newValue, oldValue) => {
		console.log("person-deep")
		console.log(newValue)
	}, {
		deep: true,
		immediate: true, // 立即执行监听，粘性
		// once: true //当 `source` 变化时，仅触发一次
	})
	/**
	 * 下面为侦听对象中的字段
	 */
	watch(() => person.value.name, (newValue) => {
		console.log("person.name")
		console.log(newValue)
	})

	/**
	 * 同时侦听多个对象
	 */
	watch([() => person.value.name, inputText], ([newName, newText], [oldName, oldText]) => {
		console.log(`newName":${newName} oldName:${oldName}`)
		console.log(`newText":${newText} oldText:${oldText}`)
	})

	/**
	 * 侦听全部
	 */
	watchEffect(()=>{
		console.log(`watchEffect name:${person.value.name} inputText:${inputText.value}`)
	})

</script>

<style lang="scss" scoped>

</style>
