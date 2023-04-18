#### node_modules 中的版本

**问题：**Package.json中的版本，由于老项目使用cnpm安装，没有出现锁定版本，导致如果cnpm升级或者npm不能安装，包容易错

**解答：**1. 可以使用 npm i -g cnpm@7.0.0 安装指定的cnpm版本；2.可以按照跑起来的项目的node_modules 锁定Package.json中的版本

#### 控制台setTimeout使用debugger

**问题：**前端找元素的时候，有些元素鼠标一离开就消失了，无法定位到元素

**解答：**可以在控制台中使用setTimeout(()=>{debugger}, 3000)  debugger 页面静止 就能定位到该元素

#### 弹出框body也滚动

**问题：** h5端弹出框弹出后 fixed之后， body如果过长还可以滚动

**解答：**弹出弹框后 document.body.style.overflow = 'hidden' 如果还不行可以让 body fixed; 关闭弹框后恢复

#### 小程序未登录加车，登录后用sessionId自动加车

**问题：**h5端未登录加车，登录后用sessionId自动加车，浏览器自带事件，小程序端如何做

**解答：**小程序端就像取cookie一样,代码如下

```javascript
// 在封装请求 返回中取
res.cookies.forEach((row) => {
   if (row && row.indexOf('/frontier-trade-web') > -1) {
     //存/frontier-trade-web
     const JSESSIONID = row.match(`[;\s+]?${'JSESSIONID'}=([^;]*)`)?.pop()
     if (JSESSIONID) {
       minCache.set('JSESSIONID', JSESSIONID)
     }
   }
 })
// 给封装请求中给
if (minCache.get('JSESSIONID')) {
  // 后端sessionId
  //#ifndef H5
  if (request.header.cookie) {
    request.header.cookie += `;JSESSIONID=${minCache.get('JSESSIONID')}`
  } else {
    request.header.cookie = `JSESSIONID=${minCache.get('JSESSIONID')}`
  }
  //#endif
}
```

