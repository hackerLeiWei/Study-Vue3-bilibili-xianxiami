<!-- 
checked	Boolean	false	是否选中	
disabled	Boolean	false	是否禁用	抖音小程序与飞书小程序不支持
type	String	switch	样式，有效值：switch, checkbox	
color	Color	-	switch 的颜色，同 css 的 color	
@change	EventHandle	-	checked 改变时触发 change 事件，event.detail={ value:checked}
 -->
<template>
	<view class="margin-bottom">
		<view class="margin-bottom">
			<text selectable>switch: https://uniapp.dcloud.net.cn/component/switch.html</text>
		</view>
		<switch />
		<switch checked="true" style="transform:scale(0.7)" type="switch" color="#007aff" foreColor="#4cd964" />

	</view>
</template>

<script setup>

</script>

<style lang="scss">

</style>