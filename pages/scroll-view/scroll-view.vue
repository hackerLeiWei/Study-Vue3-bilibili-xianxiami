<!-- 
scroll-x	Boolean	false	允许横向滚动	
scroll-y	Boolean	false	允许纵向滚动	
upper-threshold	Number/String	50	距顶部/左边多远时（单位px），触发 scrolltoupper 事件	
lower-threshold	Number/String	50	距底部/右边多远时（单位px），触发 scrolltolower 事件	
scroll-top	Number/String		设置竖向滚动条位置	
scroll-left	Number/String		设置横向滚动条位置	
scroll-into-view	String		值应为某子元素id（id不能以数字开头）。设置哪个方向可滚动，则在哪个方向滚动到该元素	
scroll-with-animation	Boolean	false	在设置滚动条位置时使用动画过渡	
enable-back-to-top	Boolean	false	iOS点击顶部状态栏、安卓双击标题栏时，滚动条返回顶部，只支持竖向	app-nvue，微信小程序
show-scrollbar	Boolean	true	控制是否出现滚动条	App-nvue 2.1.5+
refresher-enabled	Boolean	false	开启自定义下拉刷新	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
refresher-threshold	Number	45	设置自定义下拉刷新阈值	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
refresher-default-style	String	"black"	设置自定义下拉刷新默认样式，支持设置 black，white，none，none 表示不使用默认样式	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
refresher-background	String	"#FFF"	设置自定义下拉刷新区域背景颜色	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
refresher-triggered	Boolean	false	设置当前下拉刷新状态，true 表示下拉刷新已经被触发，false 表示下拉刷新未被触发	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
enable-flex	Boolean	false	启用 flexbox 布局。开启后，当前节点声明了 display: flex 就会成为 flex container，并作用于其孩子节点。	微信小程序 2.7.3、小红书小程序
scroll-anchoring	Boolean	false	开启 scroll anchoring 特性，即控制滚动位置不随内容变化而抖动，仅在 iOS 下生效，安卓下可参考 CSS overflow-anchor 属性。	微信小程序 2.8.2
@scrolltoupper	EventHandle		滚动到顶部/左边，会触发 scrolltoupper 事件	
@scrolltolower	EventHandle		滚动到底部/右边，会触发 scrolltolower 事件	
@scroll	EventHandle		滚动时触发，event.detail = {scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY}	
@refresherpulling	EventHandle		自定义下拉刷新控件被下拉	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
@refresherrefresh	EventHandle		自定义下拉刷新被触发	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
@refresherrestore	EventHandle		自定义下拉刷新被复位	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+、小红书小程序
@refresherabort	EventHandle		自定义下拉刷新被中止	H5、app-vue 2.5.12+,微信小程序基础库2.10.1+ 
-->
<template>
	<view class="margin-bottom">
		<navigator url="/pages/index/index" open-type="navigateBack">返回</navigator>
	</view>
	<view class="margin-bottom">
		<text>表单组件 button: https://uniapp.dcloud.net.cn/component/button.html</text>
	</view>
	<view class="margin-bottom"><text>纵向 scroll-view ，设置 scroll-y，height</text></view>
	<scroll-view class="layout-scroll-view" scroll-y>
		<scroll-view class="scroll-view-vertical" scroll-y>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
		</scroll-view>
		<view class="margin-bottom"><text>横向 scroll-view ，设置 scroll-x,white-space: nowrap,display: inline-block</text>
		</view>
		<scroll-view class="scroll-view-horizontal" scroll-x>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
			<view class="box">hello</view>
		</scroll-view>
	</scroll-view>
</template>

<script setup>

</script>

<style lang="scss" scoped>
	.layout-scroll-view {
		height: 100%;
		background-color: gray;
	}

	.scroll-view-vertical {
		width: 80%;
		height: 300rpx;
		background-color: white;
		border: 1rpx solid red;

		.box {
			width: 100rpx;
			height: 100rpx;
			background-color: green;
			display: block;
		}
	}

	.scroll-view-horizontal {
		width: 80%;
		background-color: white;
		border: 1rpx solid red;
		white-space: nowrap; // 不换行

		.box {
			width: 100rpx;
			height: 100rpx;
			background-color: green;
			margin: 0 5rpx;
			display: inline-block; // 默认是  block，需变更为行级块展示、一行展示，
		}
	}

</style>