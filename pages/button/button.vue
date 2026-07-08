<!-- 
size	String	default	按钮的大小		
type	String	default	按钮的样式类型		
plain	Boolean	false	按钮是否镂空，背景色透明		
disabled	Boolean	false	是否禁用		
loading	Boolean	false	名称前是否带 loading 图标		H5、App(App-nvue 平台，在 ios 上为雪花，Android上为圆圈)
form-type	String		用于 <form> 组件，点击分别会触发 <form> 组件的 submit/reset 事件		
open-type	String		开放能力		
hover-class	String	button-hover	指定按钮按下去的样式类。当 hover-class="none" 时，没有点击态效果		App-nvue 平台暂不支持
hover-start-time	Number	20	按住后多久出现点击态，单位毫秒		
hover-stay-time	Number	70	手指松开后点击态保留时间，单位毫秒		
app-parameter	String		打开 APP 时，向 APP 传递的参数，open-type=launchApp时有效		微信小程序、QQ小程序
hover-stop-propagation	boolean	false	指定是否阻止本节点的祖先节点出现点击态		微信小程序
lang	string	'en'	指定返回用户信息的语言，zh_CN 简体中文，zh_TW 繁体中文，en 英文。		微信小程序
session-from	string		会话来源，open-type="contact"时有效		微信小程序
send-message-title	string	当前标题	会话内消息卡片标题，open-type="contact"时有效		微信小程序
send-message-path	string	当前分享路径	会话内消息卡片点击跳转小程序路径，open-type="contact"时有效		微信小程序
send-message-img	string	截图	会话内消息卡片图片，open-type="contact"时有效		微信小程序
show-message-card	boolean	false	是否显示会话内消息卡片，设置此参数为 true，用户进入客服会话会在右下角显示"可能要发送的小程序"提示，用户点击后可以快速发送小程序消息，open-type="contact"时有效		微信小程序
group-id	String		打开群资料卡时，传递的群号	open-type="openGroupProfile"	QQ小程序
guild-id	String		打开频道页面时，传递的频道号	open-type="openGuildProfile"	QQ小程序
public-id	String		打开公众号资料卡时，传递的号码	open-type="openPublicProfile"	QQ小程序
data-im-id	String		客服的抖音号	open-type="im"	抖音小程序2.68.0版本+
data-im-type	String		IM卡片类型	open-type="im"	抖音小程序2.80.0版本+
data-goods-id	String		商品的id，仅支持泛知识课程库和生活服务商品库中的商品	open-type="im"	抖音小程序2.80.0版本+
data-order-id	String		订单的id，仅支持交易2.0订单	open-type="im"	抖音小程序2.80.0版本+
data-biz-line	String		商品类型，“1”代表生活服务，“2”代表泛知识。	open-type="im"	抖音小程序2.80.0版本+
contact-type	String		客服类型，默认值 seller		小红书小程序
contact-id	String		contact-type 对应的key。contact-type 为 seller 时非必传；goods 时第三方商品 id；order时第三方订单 id。open-type=contact时有效		小红书小程序
@getphonenumber	Handler		获取用户手机号回调	open-type="getPhoneNumber"	微信、支付宝、百度、抖音、快手、京东小程序、小红书小程序
@getuserinfo	Handler		用户点击该按钮时，会返回获取到的用户信息，从返回参数的detail中获取到的值同uni.getUserInfo	open-type="getUserInfo"	微信、QQ、百度、快手、京东小程序、小红书小程序
@error	Handler		当使用开放能力时，发生错误的回调	open-type="launchApp"	微信、QQ、快手、京东小程序
@opensetting	Handler		在打开授权设置页并关闭后回调	open-type="openSetting"	微信、QQ、百度、快手、京东小程序、小红书小程序
@launchapp	Handler		从小程序打开 App 成功的回调	open-type="launchApp"	微信、QQ、快手、京东小程序
@contact	Handler		客服消息回调	open-type="contact"	微信、QQ、百度、快手小程序
@chooseavatar	Handler		获取用户头像回调	open-type="chooseAvatar"	微信、支付宝小程序
@agreeprivacyauthorization	Handler		用户同意隐私协议事件回调，open-type="agreePrivacyAuthorization"时有效	open-type="agreeprivacyauthorization"	微信小程序2.32.3
@addgroupapp	Handler		添加群应用的回调	open-type="addGroupApp"	QQ小程序
@chooseaddress	Handler		调起用户编辑并选择收货地址的回调	open-type="chooseAddress"	百度小程序
@chooseinvoicetitle	Handler		用户选择发票抬头的回调	open-type="chooseInvoiceTitle"	百度小程序
@subscribe	Handler		订阅消息授权回调	open-type="subscribe"	百度小程序
@login	Handler		登录回调	open-type="login"	百度小程序
@im	Handler		监听跳转IM的成功回调	open-type="im" 
-->
<template>
	<view class="margin-bottom">
		<text>表单组件 button: https://uniapp.dcloud.net.cn/component/button.html</text>
	</view>
	<button size="mini" type="default" loading plain form-type="submit" open-type="launchApp">按钮</button>
</template>

<script setup>

</script>

<style lang="scss" scoped>
	
</style>