<template>
	<view class="margin-bottom">
		<text class="title">v-for 列表渲染</text>
	</view>
	<view class="margin-bottom background-clock">
		<!-- key 需要在当前所有子组件中唯一 -->
		<text class="margin-bottom">v-for="(item, index) in 5" 此处 item 的初值是从 1 开始而非 0</text>
		<view class="margin-bottom" v-for="(item, index) in 5" :key="item.key">
			item = {{item}} index = {{index}}
		</view>
	</view>
	<view class="margin-bottom background-clock">
		<view class="margin-bottom" v-for="(player, index) in nbaPlayers" :key="player.key">
			Player:{{player.name}} Number:{{player.num}}
		</view>
	</view>
	<text class="margin-bottom">v-for :key 不适合使用 index，如果删除或插入新数据会导致内部组件状态异常</text>
	<view class="margin-bottom background-clock">
		<checkbox-group v-on:change="itemChanged">
			<view class="layout-horizontal out" v-for="(good, index) in goods" v-bind:key="good.key">
				<label>
					<checkbox v-bind:value="good.key"></checkbox>
					<text class="">{{good.name}}</text>
					<text class="">{{good.price}}</text>
				</label>
				<text class="delete" @click="delGood(index)">删除</text>
			</view>
		</checkbox-group>
		<view class="margin-bottom">选中{{count}}个商品，一共{{money}}钱</view>
		<view class="margin-bottom">
			<button v-on:click="addGood" type="primary" v-bind:disabled="goods.length===4">新增数据</button>
		</view>
	</view>
</template>

<script setup>
	import {
		computed,
		ref
	} from 'vue'

	const goods = ref([{
			key: '100',
			name: "小米",
			price: 4000
		},
		{
			key: '200',
			name: "谷歌",
			price: 4000
		},
		{
			key: '300',
			name: "苹果",
			price: 8000
		},
		{
			key: '400',
			name: "三星",
			price: 6000
		}
	])
	const nbaPlayers = ref([{
			name: "乔丹",
			num: 23,
			key: 1
		},
		{
			name: "科比",
			num: 24,
			key: 2
		},
		{
			name: "詹姆斯",
			num: 6,
			key: 3
		},
	])

	const selectedKeyArr = ref([])

	const delGood = (index) => {
		// startIdx： 0或正数：从前到后正序；负数：从后到前倒叙
		// deleteCount：要删除的数量，0表示不删除，省略会直接删光后面所有
		// args1、args2、args3 ：要新增的各个元素
		goods.value.splice(index, 1)
	}

	const addGood = () => {
		if (goods.value.length == 4) {
			console.log("addGood return")
			return
		}
		//map
		// 参数：currentValue（当前元素，必填）、index（索引，可选）、arr（原数组，可选）。
		// 核心原则：不修改原数组，返回一个新数组。
		// const newArray = array.map(function(currentValue, index, arr) {
		//   // 必须 return 一个值，用于组成新数组
		// }, thisArg);

		// 1. ⚠️ 修改原数组的方法（变异方法）
		// 使用这些方法时，原数组会被改变，需要格外小心。
		// push(el)	末尾添加	新数组长度
		// pop()	末尾删除	删除的元素
		// unshift(el)	开头添加	新数组长度
		// shift()	开头删除	删除的元素
		// splice(start, count, ...items)	任意位置增删改	被删除的元素（数组）
		// reverse()	反转顺序	反转后的原数组（引用）
		// sort(compareFn)	排序	排序后的原数组（引用）
		// fill(value, start, end)	填充	修改后的原数组

		// 2. ✨ 返回新数组的方法（纯函数，最常用）
		// 这些方法不会动原数组，适合链式调用。
		// map(fn)	映射转换	长度不变，必须 return
		// filter(fn)	过滤筛选	返回 true 的元素保留
		// slice(start, end)	截取片段	左闭右开，不传参可实现浅拷贝
		// concat(arr)	合并数组	也可用扩展运算符 [...arr1, ...arr2]
		// flat(deep)	扁平化	默认拍平一层，传 Infinity 全拍平
		// flatMap(fn)	先 map 再 flat(1)	适合一对多映射（如拆分字符串）

		// 3. 🔍 查找与判断（不修改原数组）
		// API	作用	返回值
		// find(fn)	找到第一个满足条件的元素	元素本身（找不到返回 undefined）
		// findIndex(fn)	找到第一个满足条件的索引	索引（找不到返回 -1）
		// indexOf(el)	查找基本类型元素的索引	索引（找不到返回 -1）
		// includes(el)	是否包含某元素	boolean（比 indexOf 更语义化）
		// some(fn)	是否存在至少一个满足条件	boolean（类似逻辑或）
		// every(fn)	是否所有元素都满足条件	boolean（类似逻辑与）

		// 4. ♻️ 遍历执行副作用（不返回值）
		// API	作用	返回值
		// forEach(fn)	单纯循环，执行副作用（如打印、DOM操作）	undefined
		// keys()	返回索引迭代器	迭代器对象
		// values()	返回值迭代器	迭代器对象
		// entries()	返回 [索引, 值] 迭代器	迭代器对象（配合 for...of 使用）

		// 5. 📦 归并与转换
		// API	作用	关键点
		// reduce(fn, init)	累积计算（求和、分组、去重）	务必设置初始值，避免空数组报错
		// reduceRight(fn, init)	从右向左累积	场景较少（如多项式计算）
		// join(separator)	将数组拼成字符串	默认以 , 分隔
		// toString()	转成字符串	元素用逗号分隔

		// 6. 🛠️ 静态工具方法（Array.xxx）
		// API	作用	经典场景
		// Array.isArray(arr)	判断是否为数组	替代 typeof（typeof [] 返回 object）
		// Array.from(iterable)	将类数组/可迭代对象转为数组	转换 NodeList、arguments、Set
		// Array.of(...items)	基于参数创建数组	解决 new Array(3) 创建空位数组的歧义

		// 💡 面试/实战高频“二选一”避坑
		// splice vs slice（生死攸关）

		// splice 改原数组（删减）；slice 不改原数组（截取）。口诀：拼写短的（splice）更暴力，会改数组。

		// map vs forEach
		// 需要生成新数据用 map；单纯循环（如 console.log）用 forEach。

		// some vs find
		// 只关心“有没有”用 some（返回布尔值）；需要拿到具体元素用 find。

		// reduce 必须给初始值：

		// javascript
		// // ❌ 坏习惯：空数组没初始值会报错
		// [].reduce((a, b) => a + b); // TypeError
		// // ✅ 好习惯：永远给初始值
		// [].reduce((a, b) => a + b, 0); // 返回 0
		// sort 必须传比较函数：

		// javascript
		// // ❌ 错误：[1, 10, 2] 默认按字符串排 -> [1, 10, 2]
		// [1, 10, 2].sort();
		// // ✅ 正确：数字升序
		// [1, 10, 2].sort((a, b) => a - b); // [1, 2, 10]

		const keys = goods.value.map(good => good.key)
		let existKey = keys.includes('100')
		console.log(`存在小米 :${existKey}`)
		if (!existKey) {
			goods.value.splice(0, 0, {
				key: '100',
				name: "小米",
				price: 4000
			})
		}
		existKey = keys.includes('200')
		console.log(`存在谷歌 :${existKey}`)
		if (!existKey) {
			goods.value.splice(1, 0, {
				key: '200',
				name: "谷歌",
				price: 4000
			})
		}
		existKey = keys.includes('300')
		console.log(`存在苹果 :${existKey}`)
		if (!existKey) {
			goods.value.splice(2, 0, {
				key: '300',
				name: "苹果",
				price: 8000
			})
		}
		existKey = keys.includes('400')
		console.log(`存在三星 :${existKey}`)
		if (!existKey) {
			goods.value.splice(3, 0, {
				key: '400',
				name: "三星",
				price: 6000
			})
		}
	}

	const itemChanged = (group) => {
		selectedKeyArr.value = group.detail.value
		console.log(selectedKeyArr)
	}

	const count = computed(() => selectedKeyArr.value.length)
	const money = computed(() => {
		console.log("selectedKeyArr")
		console.log(selectedKeyArr)
		if (selectedKeyArr.value.length) {
			const checkedGoods = goods.value.filter( /*(good, indexGood, arrayGood)*/ good => selectedKeyArr.value
				.some( /*(key, index, array)*/ key => key === good.key))
			console.log("checkedGoods")
			console.log(checkedGoods)
			//参数说明：0 是初始值，如果不写，会默认取数组第一项（但若数组为空会报错，建议写 0）。
			return checkedGoods.map(good => good.price).reduce((previousTotal, current) => previousTotal + current,
				0)
		}
		return 0
	})
</script>

<style lang="scss" scoped>
	.out {
		padding: 20rpx;

		.delete {
			color: red;
			margin-left: 20rpx;
		}
	}
</style>
