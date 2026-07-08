<!-- 
min	Number	0	最小值
max	Number	100	最大值
step	Number	1	步长，取值必须大于 0，并且可被(max - min)整除
disabled	Boolean	false	是否禁用
value	Number	0	当前取值
activeColor	Color	各个平台不同，详见下	滑块左侧已选择部分的线条颜色
backgroundColor	Color	#e9e9e9	滑块右侧背景条的颜色
block-size	Number	28	滑块的大小，取值范围为 12 - 28
block-color	Color	#ffffff	滑块的颜色
show-value	Boolean	false	是否显示当前 value
@change	EventHandle		完成一次拖动后触发的事件，event.detail = {value: value}
@changing	EventHandle		拖动过程中触发的事件，event.detail = {value: value} 
-->
<template>
	<view class="margin-bottom">
		<text selectable>slider: https://uniapp.dcloud.net.cn/component/slider.html</text>
	</view>

	<view class="layout-vertical">
		<view class="margin-bottom">
			<slider></slider>
		</view>
		<view class="margin-bottom">
			<slider value="30" activeColor="#007aff" backgroundColor="#c0c0c0" block-size="20" show-value
				block-color="#dd524d"></slider>
		</view>
	</view>
</template>

<script setup>

</script>

<style lang="scss">

</style>