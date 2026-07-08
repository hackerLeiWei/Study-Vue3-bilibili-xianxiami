<template>
	<text class="title margin-bottom">Vue3 学：ref 、 function</text>
	<view class="margin-bottom">
		<text>{{5+5}} -- {{Date.now()}} -- {{PI}} -- {{Math.random()}}</text>
	</view>
	<view class="margin-bottom">
		<text>{{PI > 3 ?"李四":"张三"}}</text>
	</view>
	<view class="margin-bottom">
		<text>PI * PI = {{powerPI()}}</text>
	</view>
	<view class="margin-bottom">
		<text>PI + PI = {{plusPI()}}</text>
	</view>
	<view class="margin-bottom">
		<text>计数器: {{count}}</text>
	</view>
	<view class="margin-bottom">
		<text>绑定计数器: {{countRef}}</text>
	</view>
	<view class="margin-bottom">
		<text>绑定字符串: {{textRef}}</text>
	</view>
	<view class="margin-bottom">
		<text>绑定数组: [{{arrRef.join(",")}}]</text>
	</view>
	<view class="margin-bottom">
		<text>绑定数组元素: {{arrRef[1]}}</text>
	</view>
	<view class="margin-bottom">
		<text>绑定对象: {{objRef}}</text>
	</view>
	<view class="margin-bottom">
		<text>绑定对象属性:  {{objRef.name}} {{objRef.age}}</text>
	</view>

</template>

<script setup>
	import {
		ref
	} from 'vue'

	const PI = Math.PI
	let count = 0
	let countRef = ref(0) // 改变此值，会导致引用该属性的组件重新渲染
	let textRef = ref("来自js的字符串，可变动") // 改变此值，会导致引用该属性的组件重新渲染
	let arrRef = ref([1, 2, 3, 4]) // let const 都可以修饰
	let objRef = ref({
		name: "张三",
		age: 20
	})

	setInterval(() => {
		count++
		countRef.value += 2
		console.log(`count ${count}`)
		console.log(`countRef ${countRef.value}`)
		arrRef.value[1] += 1
		// for (let idx = 0 idx < arrRef.value.length, idx++) {
		// 	arrRef.value[idx] += 1
		// }
		objRef.value.age += 1
	}, 2000)

	console.log(`count ${count}`)
	console.log(`countRef ${countRef.value}`)

	function powerPI() {
		return PI * PI
	}

	const plusPI = () => {
		return PI + PI
	}
</script>

<style lang="scss" scoped>

</style>