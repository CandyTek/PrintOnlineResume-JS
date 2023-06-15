## 一个油猴脚本：打印在线简历网站 - 打印时优化排版。

已支持多个网站：超级简历、全民简历

欢迎 Star, Fork

### 免责声明 

本脚本中提供的所有功能均仅在浏览器中运行，所使用的源代码公开透明可见，且本脚本仅学习研究使用，不使用任何盈利方案或参与任何盈利组织，因使用本脚本引起的或与本脚本有关的任何争议，各方应友好协商解决，本脚本对使用本脚本所提供的软件时可能对用户自己或他人造成的任何形式的损失和伤害不承担任何责任。如用户下载、安装和使用本产品中所提供的软件，即表明用户信任本作者及其相关协议和免责声明。

```js
// ==UserScript==
// @name         【超级简历】【全民简历】- 打印网页时优化排版
// @note         // ██ 注意 注意 ██：使用快捷键 Ctrl + L 打印网页
// @note         // ██ 注意 注意 ██：使用快捷键 Ctrl + L 打印网页
// @note         // ██ 注意 注意 ██：使用快捷键 Ctrl + L 打印网页
// @note         // ██ 注意 注意 ██：使用快捷键 Ctrl + L 打印网页
// @note         // ██ 注意 注意 ██：使用快捷键 Ctrl + L 打印网页
// @namespace    http://tampermonkey.net/
// @version      1.3
// @description  █注意：仅作为个人打印网页使用，不得用作其他用途，违法必究。使用快捷键 Ctrl + L 打印网页
// @license      MIT
// @author       AiniyoMua
// @home-url     https://greasyfork.org/zh-CN/scripts/460387
// @homepageURL  https://greasyfork.org/zh-CN/scripts/460387
// @supportURL   https://greasyfork.org/zh-CN/scripts/460387/feedback
// @match        *://www.wondercv.com/cvs/*
// @match        *://www.qmjianli.com/cv/edit/*
// @run-at       document-start
// @icon         data:image/png;base64,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
// @grant        GM_addStyle
// ==/UserScript==
(function() {
	if(window.location.hostname.includes("wondercv")){							wondercv();
	}else if(window.location.hostname.includes("qmjianli")){					qmjianli();
	}

function wondercv() {
	// 左侧栏
	// 简历上面的样式编辑框
	// 下面悬浮的 页数框
	// 右下角悬浮按钮
	// 右下角悬浮按钮
	// 顶栏
	// 顶栏
	// 简历正文上面黑黑一条的东西
	// 简历正文右上角字数框
	// 简历正文把高度拉满，使其不要缩在滚动条框内
	// 简历正文把高度拉满
	// 正文细节纠正
	// 正文因为有transform这个属性，所以div框是智能适配宽度的，必须得去掉
	// 正文宽度调整，更改背景色为白色
	// 正文左边margin去掉
	// 简历正文把高度拉满
	var css = `
		div.sidebar-side-content {display:none !important;}
		div.cvs > div:nth-child(1) {display:none !important;}
		div.cvs > div.resume-pagination {display:none !important;}
		#phone-code {display:none !important;}
		#udesk_container {display:none !important;}
		.nav-container {display:none !important;}
		.pc-nav {display:none !important;}
		.header-line {display:none !important;}
		.cv-font-number {display:none !important;}
		div.resume.a4.one-page-bottom{height:100% !important;}
		.cvs-component {max-height:100% !important;}
		.edit-cv-main {
			padding-top:0px !important;
			height:100% !important;
			width:100% !important;
			min-width:0px !important;
			justify-content:flex-start !important;
			padding: 0px 0px 0 !important;
			display:block !important;
		}
		div.scale.visible {width:100% !important;transform:none !important;}
		.cv-editor-main{min-width: 0px !important;background-color: #fff !important;}
		div.cvs {margin-left: 0px !important;}
		.resume.a4{height:100% !important;}
	`
	var multiPage = `div.cv-editor-main{height:100% !important;}`
		// 注册按键事件
	document.onkeydown =cdk;
	function cdk(){
		// 快捷键：Ctrl + L
		if (window.event.ctrlKey && window.event.keyCode==76 && !window.event.altKey && !window.event.shiftKey){
			GM_addStyle(css);
			// 如果需要打印多张页数，把下面这一行注释取消：
			// GM_addStyle(multiPage);
			// 可调整下面的值并把下面这一行注释取消，以调整简历正文的宽度：
			// GM_addStyle(`div.cvs {max-width: 1000px !important;}`);
			setTimeout(function(){window.print();}, 400);	// 延迟 0.4s 打印网页
		}
	}


}

function qmjianli(){
	// 网页的顶栏
	// 网页底部的编辑栏
	// 网页右下角悬浮栏
	// 网页顶部下载按钮
	// 正文顶部页数显示
	// 网页右边栏
	// 去掉正文上面的padd，调整正文宽度
	// 去掉正文上面的padd，调整正文宽度，更改背景色
	var css = `
		div.edit_header {display:none !important;}
		div.edit_all {display:none !important;}
		div.float_r {display:none !important;}
		div.down_big {display:none !important;}
		ul.page_line {display:none !important;}
		div.edit_fixed {display:none !important;}
		div.edit_main {padding-top:0px !important;width: 100% !important;}
		section.edit_resume {padding-top:0px !important;min-width: 0px !important;background-color: #fff !important;}
	`
	function cdk(){
		// 快捷键：Ctrl + L
		if (window.event.ctrlKey && window.event.keyCode==76 && !window.event.altKey && !window.event.shiftKey){
			GM_addStyle(css);
			setTimeout(function(){window.print();}, 400);	// 延迟 0.4s 打印网页
		}
	}
}

	// 最后做一下备注：
	// 简历超人，免费下载，https://jlcr.haitou.cc/
})();
```
