<!-- 
value	String		<radio> 标识。当该 <radio> 选中时，<radio-group> 的 change 事件会携带 <radio> 的 value	
checked	Boolean	false	当前是否选中	
disabled	Boolean	false	是否禁用	
color	Color		radio的颜色，同css的color	
backgroundColor	Color	#ffffff	radio默认的背景颜色	H5(3.99+)、App-Vue(3.99+)
borderColor	Color	#d1d1d1	radio默认的边框颜色	H5(3.99+)、App-Vue(3.99+)
activeBackgroundColor	Color	#007AFF	radio选中时的背景颜色，优先级大于color属性	H5(3.99+)、App-Vue(3.99+)
activeBorderColor	Color		radio选中时的边框颜色	H5(3.99+)、App-Vue(3.99+)
iconColor	Color	#ffffff	radio的图标颜色	H5(3.99+)、App-Vue(3.99+) 
-->
<template>
	<view class="margin-bottom">
		<text selectable>radio-group: https://uniapp.dcloud.net.cn/component/radio.html</text>
	</view>
	<view class="margin-bottom"><text>
			value、checked、color、backgroundColor、activeBackgroundColor、borderColor、activeBorderColor </text></view>
	<radio-group class="layout-vertical">
	<view class="margin-bottom"><text>
			activeBackgroundColor > color </text></view>
	<radio-group class="layout-vertical">
		<radio class="margin-bottom" value="男" checked color="#ff0000" backgroundColor="#f0f0f0"
			activeBackgroundColor="#ff00ff" borderColor="#333" activeBorderColor="#00ff00" />
		<radio class="margin-bottom" value="女" />
	</radio-group>
</template>

<script setup>

</script>

<style lang="scss">


</style>