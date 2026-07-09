<template>
	<view class="title">
		列表demo
	</view>
	<view class="page">
		<view class="list">
			<view class="item" v-for="(item, index) in items" :key="item.key">
				<!-- 序号 -->
				<view class="index">{{ index + 1 }}</view>
				<view class="content">{{ item.content }}</view>
				<icon class="icon" type="clear" size="26rpx" v-on:click="close(index)" />
			</view>
		</view>
		<view class="count">
			一共{{items.length}}条数据
		</view>
		<view class="comment">
			<input ref="input" class="input" placeholder="请输入：" v-model="inputContent" maxlength="50" />
			<button class="button" size="mini" v-bind:disabled="!inputContent.length" type="primary"
				v-on:click="publish">发布</button>
		</view>
	</view>
</template>

<script setup>
	import {
		ref
	} from 'vue'
	const input = ref(null)
	const inputContent = ref("")

	const items = ref([{
			key: 10,
			content: "你今年多少岁？"
		},
		{
			key: 11,
			content: "我今年刚刚18"
		},
		{
			key: 12,
			content: "遥遥领先"
		},
		{
			key: 13,
			content: "这这么贵了？"
		}
	])

	const close = (index) => {
		uni.showModal({
			title: `提示`,
			content: `是否删除 [${items.value[index].content}]`,
			confirmColor: "#ff0000",
			success: (res) => {
				if (res.confirm) {
					items.value.splice(index, 1)
				} else {

				}
			}
		})
	}
	const publish = () => {
		const key = items.value.length > 0 ? items.value[items.value.length - 1].key : 10
		console.log(`key : ${key}`)
		items.value.push({
			key: key,
			content: inputContent.value
		})
		inputContent.value = ""
	}
</script>

<style lang="scss" scoped>
	.page {
		width: 90vw;
		margin: 5vw;
		box-shadow: 0 10rpx 20rpx rgba(0, 0, 0, 0.2);
		border-radius: 5rpx;
		padding: 15rpx;
		box-sizing: border-box;

	}

	.list {
		display: flex;
		flex-direction: column;

		.item {
			// display: flex;
			// align-items: center;
			// /* 垂直居中对齐 */
			// background-color: #ffffff;
			// // border-radius: 16rpx;
			// padding: 24rpx 30rpx;
			// margin-bottom: 24rpx;
			// box-shadow: 0 4rpx 20rpx rgba(0, 0, 0, 0.08);
			// /* 阴影效果 */

			display: flex;
			padding: 10rpx 0;
			border-bottom: 1rpx solid #dddddd;
			justify-content: center;
			align-items: center;
			font-size: 18rpx;
			color: #333333;

			.index {
				flex-shrink: 0;
				/* 固定宽度，不压缩 */
				width: 60rpx;
				text-align: center;
				font-weight: 600;
				color: #999;
				font-size: 28rpx;
			}

			.content {
				flex: 1;
				/* 占据剩余空间 */
				word-break: break-word;
				/* 允许长单词或内容换行 */
				white-space: normal;
				/* 正常换行 */
				font-size: 28rpx;
				color: #333;
				line-height: 1.6;
				margin: 0 20rpx;
				/* 与序号和图标保持间距 */
			}

		}

		.close {
			position: relative;
			margin: 0 20rpx;
			width: 40rpx;
			height: 40rpx;
		}

	}

	.count {
		padding: 10rpx 0;
		font-size: 20rpx;
		color: gray;
		text-align: center;
	}

	.comment {
		display: flex;
		margin-top: 10rpx;

		.input {
			flex: 4;
			background: #f4f4f4;
			margin-right: 5rpx;
			width: 100%;
			height: 60rpx;
			line-height: 60rpx;
			border-radius: 4rpx;
			padding: 0 10rpx;
			color: #333333;
		}

		.button {
			flex: 1;
		}
	}
</style>
