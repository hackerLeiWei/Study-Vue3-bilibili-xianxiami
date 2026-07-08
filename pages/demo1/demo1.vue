<template>
	<view><text>Image https://uniapp.dcloud.net.cn/component/image.html</text></view>

	<view><text>Image 默认RendserSize:320x240px。根据高度缩放：heightFix+height,
			根据宽度缩放：widthFix+width，完整展示，留白：aspectFit+width+height，中间裁剪：aspectFill+width+height。 支持格式：
			bmp
			gif
			ico
			jpg
			png
			webp
			heic（Android10+支持）</text></view>
	<view>
		<image src="@/static/logo.png" mode="aspectFill" style="background-color: gray;"></image>
	</view>
	<view>
		<image
			src="https://imgs-qn.51miz.com/preview/element/00/01/48/91/P-1489138-A3BDDFEC.png?imageMogr2/thumbnail/x720/quality/90|imageMogr2/format/webp"
			mode="aspectFill" style="background-color: gray;"></image>
	</view>
</template>

<script setup>

</script>

<style lang="scss">
	.cropcenter {}
</style>