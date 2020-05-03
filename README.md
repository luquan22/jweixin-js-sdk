# jwexin-ls-jdk1.6.0 bug修正版
作者:**陆权**
##js来源
https://res.wx.qq.com/open/js/jweixin-1.6.0.js

微信官方
##代码修改
!(function(e, n) { typeof define === 'function' && (define.amd || define.cmd) ? define(function() { return n(e) }) : n(e, !0) }

改为

!(function (e, n) {
    module.exports = n(e)
}
##bug修改
var i = e.document;

改为

var i = o.document;

##增加函数
config: 函数和 ready: 函数之间增加:

signurl: function() { return h.url },

##使用方法
1. npm i jweixin-1.6.0
2. 在需要分享vue组件或页面：
   
   import wx from 'jweixin-1.6.0'
   
3. 使用wx.config的函数位置，判断机型

    let signLink = ''

     const ua = navigator.userAgent.toLowerCase()
     
     if (/iphone|ipad|ipod/.test(ua)) {
     
       // 记录进入app时的url
       // alert('苹果终端设备')
       signLink = decodeURIComponent(wx.signurl())
       
     } else if (/(android)/i.test(ua)) {
     
       // alert('安卓终端设备')
       signLink = location.href
     } else {
     
       // alert('PC终端设备')
       signLink = location.href
     }

4. { url: signLink }。生成的signLink作为签名url




