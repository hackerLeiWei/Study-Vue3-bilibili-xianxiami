<!-- 
indicator-dots	Boolean	false	是否显示面板指示点	
indicator-color	Color	rgba(0, 0, 0, .3)	指示点颜色	
indicator-active-color	Color	#000000	当前选中的指示点颜色	
active-class	String		swiper-item 可见时的 class	支付宝小程序
changing-class	String		acceleration 设置为 true 时且处于滑动过程中，中间若干屏处于可见时的class	支付宝小程序
autoplay	Boolean	false	是否自动切换	
current	Number	0	当前所在滑块的 index	
current-item-id	String		当前所在滑块的 item-id ，不能与 current 被同时指定	支付宝小程序不支持、小红书小程序不支持
interval	Number	5000	自动切换时间间隔	
duration	Number	500	滑动动画时长	app-nvue不支持
circular	Boolean	false	是否采用衔接滑动，即播放到末尾后重新回到开头	
vertical	Boolean	false	滑动方向是否为纵向	
previous-margin	String	0px	前边距，可用于露出前一项的一小部分，接受 px 和 rpx 值	app-nvue、抖音小程序、飞书小程序不支持
next-margin	String	0px	后边距，可用于露出后一项的一小部分，接受 px 和 rpx 值	app-nvue、抖音小程序、飞书小程序不支持
acceleration	Boolean	false	当开启时，会根据滑动速度，连续滑动多屏	支付宝小程序
disable-programmatic-animation	Boolean	false	是否禁用代码变动触发 swiper 切换时使用动画。	支付宝小程序
display-multiple-items	Number	1	同时显示的滑块数量	app-nvue、支付宝小程序不支持、小红书小程序不支持
skip-hidden-item-layout	Boolean	false	是否跳过未显示的滑块布局，设为 true 可优化复杂情况下的滑动性能，但会丢失隐藏状态滑块的布局信息	App、微信小程序、京东小程序
disable-touch	Boolean	false	是否禁止用户 touch 操作	App 2.5.5+、H5 2.5.5+、支付宝小程序
easing-function	String	default	指定 swiper 切换缓动动画类型，有效值：default、linear、easeInCubic、easeOutCubic、easeInOutCubic	微信小程序、快手小程序、京东小程序
@change	EventHandle		current 改变时会触发 change 事件，event.detail = {current: current, source: source}	
@transition	EventHandle		swiper-item 的位置发生改变时会触发 transition 事件，event.detail = {dx: dx, dy: dy}，支付宝小程序暂不支持dx, dy	App、H5、微信小程序、支付宝小程序、抖音小程序、飞书小程序、QQ小程序、快手小程序
@animationfinish	EventHandle		动画结束时会触发 animationfinish 事件，event.detail = {current: current, source: source}	抖音小程序、飞书小程序与小红书小程序不支持 
-->
<template>
	<view><text>swiper
			轮播，indicator-dots、indicator-color、indicator-active-color、circular、autoplay、duration、interval、vertical。swiper-item:nth-child</text>
	</view>
	<swiper indicator-dots indicator-active-color="#4cd964FF" indicator-color="rgba(180,180,180,1.0)" circular autoplay
		duration="300" interval="3000">
		<swiper-item>
			<image src="/static/swiper-items/swiper-item-01.webp" mode="aspectFill"></image>
		</swiper-item>
		<swiper-item>
			<image src="/static/swiper-items/swiper-item-02.webp" mode="aspectFill"></image>
		</swiper-item>
		<swiper-item>
			<image src="/static/swiper-items/swiper-item-03.webp" mode="aspectFill"></image>
		</swiper-item>
		<swiper-item>
			<image src="/static/swiper-items/swiper-item-04.webp" mode="aspectFill"></image>
		</swiper-item>
	</swiper>
	<swiper indicator-dots indicator-active-color="#4cd964FF" indicator-color="rgba(180,180,180,1)" circular autoplay
		vertical duration="300" interval="3000">
		<swiper-item>11111111111</swiper-item>
		<swiper-item>222222222222</swiper-item>
		<swiper-item>33333333</swiper-item>
		<swiper-item>444444444</swiper-item>
	</swiper>
</template>

<script setup>

</script>

<style lang="scss" scoped>
	// swiper 标签中没有写 class 名称，可以直接这样写，建议用 scoped 指定区间
	swiper {
		width: 100vw; // vw viewport width;vh viewport height
		height: 300rpx;
		border: 1rpx solid green;

		swiper-item {
			width: 100%; // % 跟父组件对比
			height: 100%; // % 跟父组件对比
			background-color: orange;
			image{
				width: 100%;
				height: 100%;
			}
		}

		swiper-item:nth-child(2n) {
			// 伪类显示器
			background-color: pink;
		}
	}
</style>