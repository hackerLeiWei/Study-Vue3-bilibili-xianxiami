<!-- 必须放模板 -->
<template>
	<view class="layout-vertical">
		<view class="margin-bottom"><text selectable>视图容器View: https://uniapp.dcloud.net.cn/component/view.html</text>
		</view>
		<text class="margin-bottom">Vue3 组件 View
			、Text。属性：border、solid、class-hover、display、flex-direction、justify-content、align-items、margin、padding、selectable、background-color</text>
	</view>
	<!-- vue3  可以存放多个根节点， vue2 只能存在一个-->
	<view class="layout-vertical">
		<view class="box1">
			layout-vertical
		</view>
		<view class="box1">
			layout-vertical
		</view>
		<view class="box1">
			layout-vertical
		</view>
		<view class="box1">
			layout-vertical
		</view>
	</view>

	<view class="layout-vertical">
		<view class="box1">Box1</view>
		<view class="box2">Box2</view>
	</view>

	<view class="layout-lorizontal">
		<view class="box3">Box3</view>
		<view class="box4">Box4</view>
	</view>

	<view class="layout-hover-gray" hover-class="hover-orange" hover-stay-time="50">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50">
			<text>hover 点击事件，父组件设置了其自己的 hover-class ,在点击子组件时父组件也会显示hover-class</text>
		</view>
	</view>
	<!-- hover-stop-propagation 属性设置为 true 时，后面不许需要跟值，直接写属性就可以 -->
	<view class="layout-hover-gray" hover-class="hover-orange" hover-stay-time="50">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>hover 点击事件，子组件设置了 hover-class 和 hover-stop-propagation（微信小程序支持
				https://uniapp.dcloud.net.cn/component/view.html），点击子组件时父组件不会改变样式</text>
		</view>
	</view>

	<view class="margin-bottom">
		<!-- space 空格的样式 -->
		<text selectable space="emsp">可以长按 拷贝</text>
	</view>

	<view class="layout-hover-gray" style="background-color: gray; padding: 20rpx 0;" hover-class="hover-orange"
		hover-stay-time="50">
		<navigator class="layout-hover-green" url="/pages/scroll-view/scroll-view" open-type="navigate">
			<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
				<text>进入scroll-view 菜单页面</text>
			</view>
		</navigator>
	</view>
	<navigator class="layout-vertical" url="/pages/button/button" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 button 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/input/input" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 input 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/checkbox/checkbox" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 checkbox 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/radio-group/radio-group" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 radio-group 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/slider/slider" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 slider 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/switch/switch" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 switch 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/vue3/vue3" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 vue3 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/vue3/ref" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 vue3 ref 页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/vue3/v-bind" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 vue3 v-bind 属性页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/vue3/v-on" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 vue3 v-on 事件页面</text>
		</view>
	</navigator>
	<navigator class="layout-vertical" url="/pages/vue3/v-if" open-type="navigate">
		<view class="layout-hover-green" hover-class="hover-red" hover-stay-time="50" hover-stop-propagation>
			<text>进入 v-if 条件渲染页面</text>
		</view>
	</navigator>

</template>

<!-- vue3 script 标签 需要写 setup 语法糖组合式 api -->
<!-- vue2 script 标签 为选项式 api
 export default {
 	data() {
 		return {
 			title: 'Hello'
 		}
 	},
 	onLoad() {

 	},
 	methods: {

 	}
 }-->
<script>
	const toScrollViewMenu = () => {
		uni.navigateTo({
			url: "/pages/scroll-view/scroll-view"
		})
	}
</script>

<style lang="scss" scoped>
	.layout-vertical {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin-bottom: 20rpx;

		.box1 {
			border: 1rpx solid red;
		}

		.box2 {
			border: 1rpx solid green;
		}
	}

	.margin-bottom {
		margin-bottom: 20rpx;
	}

	.layout-lorizontal {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		margin-bottom: 20rpx;
	}

	.box3 {
		border: 1rpx solid red;
	}

	.box4 {
		border: 1rpx solid green;
	}

	.layout-hover-gray {
		display: flex;
		flex-direction: column;
		align-items: center;
		background-color: gray;
		padding: 80rpx 20rpx;
		margin-bottom: 20rpx;
	}

	.layout-hover-green {
		margin-bottom: 20rpx;
		padding: 0 20rpx;
		background-color: green;
	}

	.hover-orange {
		background-color: orange;
	}

	.hover-red {
		background-color: red;
	}

	/* .content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	} */
</style>