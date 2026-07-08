<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	.layout-vertical {
		display: flex;
		flex-direction: column;
		padding: 20rpx;
	}
	.layout-horizontal {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 20rpx;
	}

	.title {
		font-size: 50rpx;
		color: black;
	}

	.margin-bottom {
		margin-bottom: 20rpx;
	}

	.uni-input-wrapper {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		flex-wrap: nowrap;
	}

	.uni-icon {
		font-family: uniicons;
		font-size: 24px;
		font-weight: normal;
		font-style: normal;
		width: 24rpx;
		height: 24rpx;
		line-height: 24px;
		color: #999999;
	}
	.background-clock{
		background-color: blanchedalmond;
	}
</style>