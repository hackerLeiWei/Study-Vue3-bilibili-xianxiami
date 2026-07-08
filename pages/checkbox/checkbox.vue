<!-- 
value	String		<checkbox> 标识，选中时触发 <checkbox-group> 的 change 事件，并携带 <checkbox> 的 value。	
disabled	Boolean	false	是否禁用	
checked	Boolean	false	当前是否选中，可用来设置默认选中	
color	Color		checkbox的颜色，同css的color	
backgroundColor	Color	#ffffff	checkbox默认的背景颜色	H5(3.99+)、App-Vue(3.99+)
borderColor	Color	#d1d1d1	checkbox默认的边框颜色	H5(3.99+)、App-Vue(3.99+)
activeBackgroundColor	Color	#ffffff	checkbox选中时的背景颜色，优先级大于color属性	H5(3.99+)、App-Vue(3.99+)
activeBorderColor	Color	#d1d1d1	checkbox选中时的边框颜色	H5(3.99+)、App-Vue(3.99+)
iconColor	Color	#007aff	checkbox的图标颜色	H5(3.99+)、App-Vue(3.99+) 
-->
<template>
	<view class="margin-bottom">
		<text selectable>CheckBox: https://uniapp.dcloud.net.cn/component/checkbox.html</text>
	</view>
	<view class="margin-bottom">
		<text
			selectable>value、checked、backgroundColor、activeBackgroundColor、borderColor、activeBorderColor、foreColor</text>
	</view>
	<view class="margin-bottom">
		<text selectable>activeBackgroundColor > foreColor > color</text>
	</view>
	<view>
		<label>
			<checkbox value="你好" /><text>你好</text>
		</label>
		<label>
			<checkbox value="你好" checked backgroundColor="#f1f1f1" activeBackgroundColor="#f0ad4e" borderColor="#000000"
				activeBorderColor="#00ff00" color="#0000ff" foreColor="#ff0000" /><text>你好</text>
		</label>

	</view>

</template>

<script setup>

</script>

<style lang="scss">

</style>