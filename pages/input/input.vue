<!-- 
value	String		输入框的初始内容	
type	String	text	input 的类型 有效值	
text-content-type	String		文本区域的语义，根据类型自动填充 有效值	仅 App-nvue-iOS 支持
password	Boolean	false	是否是密码类型	H5和App写此属性时，type失效
placeholder	String		输入框为空时占位符	
placeholder-style	String		指定 placeholder 的样式	
placeholder-class	String	"input-placeholder"	指定 placeholder 的样式类，注意页面或组件的style中写了scoped时，需要在类名前写/deep/	抖音小程序、飞书小程序、快手小程序不支持
disabled	Boolean	false	是否禁用	
maxlength	Number	140	最大输入长度，设置为 -1 的时候不限制最大长度	
cursor-spacing	Number	0	指定光标与键盘的距离，单位 px 。取 input 距离底部的距离和 cursor-spacing 指定的距离的最小值作为光标与键盘的距离	App、微信小程序、百度小程序、QQ小程序、京东小程序
focus	Boolean	false	获取焦点。	H5、App需要点击按钮获取焦点的，必须使用@touchend.prevent="onTap"阻止键盘收起默认事件才能获取焦点关于软键盘弹出的逻辑说明，小程序、nvue需使用组件的 focus()、blur() 方法控制焦点
confirm-type	String	done	设置键盘右下角按钮的文字，仅在 type="text" 时生效。有效值	微信小程序、App、H5、快手小程序、京东小程序、小红书小程序
confirm-hold	Boolean	false	点击键盘右下角按钮时是否保持键盘不收起	App(3.3.7+)、H5 (3.3.7+)、微信小程序、支付宝小程序、百度小程序、QQ小程序、京东小程序、小红书小程序
cursor	Number		指定focus时的光标位置	
cursor-color	String		光标颜色	微信小程序 3.1.0+、H5(4.0+)、App-Vue(4.0+)
selection-start	Number	-1	光标起始位置，自动聚集时有效，需与selection-end搭配使用	
selection-end	Number	-1	光标结束位置，自动聚集时有效，需与selection-start搭配使用	
adjust-position	Boolean	true	键盘弹起时，是否自动上推页面	App-Android（vue 页面 softinputMode 为 adjustResize 时无效，使用 x5 内核时无效）、微信小程序、百度小程序、QQ小程序、京东小程序、小红书小程序
auto-blur	Boolean	false	键盘收起时，是否自动失去焦点	App-Vue 3.0.0+
ignoreCompositionEvent	Boolean	true	是否忽略组件内对文本合成系统事件的处理。为 false 时将触发 compositionstart、compositionend、compositionupdate 事件，且在文本合成期间会触发 input 事件	App-vue (3.4.4+)、H5 (3.4.4+)、App-nvue不支持
always-embed	Boolean	false	强制 input 处于同层状态，默认 focus 时 input 会切到非同层状态 (仅在 iOS 下生效)	微信小程序 2.10.4+
hold-keyboard	Boolean	false	focus时，点击页面的时候不收起键盘	微信小程序 2.8.2+
safe-password-cert-path	String		安全键盘加密公钥的路径，只支持包内路径	微信小程序 2.18.0+
safe-password-length	Number		安全键盘输入密码长度	微信小程序 2.18.0+
safe-password-time-stamp	Number		安全键盘加密时间戳	微信小程序 2.18.0+
safe-password-nonce	String		安全键盘加密盐值	微信小程序 2.18.0+
safe-password-salt	String		安全键盘计算 hash 盐值，若指定custom-hash 则无效	微信小程序 2.18.0+
safe-password-custom-hash	String		安全键盘计算 hash 的算法表达式，如 md5(sha1('foo' + sha256(sm3(password + 'bar'))))	微信小程序 2.18.0+
random-number	Boolean	false	当 type 为 number, digit, idcard 数字键盘是否随机排列	支付宝小程序 1.9.0+
controlled	Boolean	false	是否为受控组件。为 true 时，value 内容会完全受 setData 控制	支付宝小程序 1.9.0+
always-system	Boolean	false	是否强制使用系统键盘和 Web-view 创建的 input 元素。为 true 时，confirm-type、confirm-hold 可能失效	支付宝小程序 2.7.3+
inputmode	String	"text"	是一个枚举属性，它提供了用户在编辑元素或其内容时可能输入的数据类型的提示。有效值	H5（3.6.16+）、App-vue（3.6.16+）
@input	EventHandle		当键盘输入时，触发input事件，event.detail = {value}	差异见下方 Tips
@focus	EventHandle		输入框聚焦时触发，event.detail = { value, height }，height 为键盘高度	仅微信小程序、京东小程序、App（2.2.3+） 、QQ小程序、快手小程序支持 height、小红书小程序
@blur	EventHandle		输入框失去焦点时触发，event.detail = {value: value}	
@confirm	EventHandle		点击完成按钮时触发，event.detail = {value: value}	
@keyboardheightchange	eventhandle		键盘高度发生变化的时候触发此事件，event.detail = {height: height, duration: duration}	微信小程序基础库2.7.0+、App 3.1.0+ 
-->
<template>
	<view class="margin-bottom">
		<text>表单组件 input: https://uniapp.dcloud.net.cn/component/input.html</text>
	</view>
	<view class="margin-bottom">
		<text>type、placeholder、cursor、cursor-color、selection-start、selection-end、auto-blur、random-number、confirm-type、password、maxlength</text>
	</view>
	
	<view class="margin-bottom">
		<input placeholder="请输入内容" type="text" value="输入框默认值" cursor="4" cursor-color="rgba(255,0,0,1.0)" selection-start="1" selection-end="3" auto-blur/>
		<input placeholder="请输入邮箱" type="email"/>
		<input placeholder="请输入身份证" type="idcard"/>
		<input placeholder="请输入数字" type="number"/>
		<input placeholder="请输入小数点数字，键盘数字随机排列" type="digit" random-number/>
		<input placeholder="请输入小数点数字带分隔符，键盘数字随机排列" type="decimal" random-number/>
		<input placeholder="请输入电话" type="tel"/>
		<input placeholder="请输入密码" type="text" password maxlength="16"/>
		<input placeholder="请输入内容 密码安全输入键盘" type="safe-password"/>
		<input placeholder="请输入搜索内容" type="search" confirm-type="search"/>
		<input placeholder="请输入最后一项内容" confirm-type="done"/>
		<input placeholder="请输入内容，下一步" confirm-type="next"/>
		<input placeholder="请输入内容，发送" confirm-type="send"/>
		<view class="uni-input-wrapper">
			<input placeholder="请输入内容，GO" confirm-type="go">
			<text class="uni-icon" >&#xe434;</text>
		</view>
		
	</view>
</template>

<script setup>
	
</script>

<style>
	
</style>
