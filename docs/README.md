> Welcome to utils !

项目工具函数整理，支持搜索，方便使用~

<!-- > 使用 -->


- 全局引入



1. 新建utils/index.js文件夹
```javascript
module.exports = {
  // ...
}
```
2. main.js引入
```javascript
// 引入
import Tools from "@/utils"
// 挂载
Vue.prototype.$tools = Tools //工具函数
```
3. 项目中使用
```javascript
this.$tools.navTo(arguments)
```


- 局部引入



1. 新建utils/index.js文件夹
```javascript
module.exports = {
  // ...
}
```
2. .vue引入和使用
```javascript
// 引入
import { fn } from "@/utils"
// 使用
fn()
```
