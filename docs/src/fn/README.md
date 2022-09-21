   ## 节流函数 
  ```javascript
	/**
	 *@param { Fcuntion } fn 节流被执行函数 
	 *@param { Number }  delay 时间单位内
	 */
	throttle(fn, delay) {
		let flag = true,
			timer = null;
		return function(...args) {
			let context = this
			if (!flag) return
			flag = false
			clearTimeout(timer)
			timer = setTimeout(() => {
				fn.apply(context, args)
				flag = true
			}, delay)
		}
	},
	```
   ## 防抖函数 
  ```javascript
	/**
	 *@param { Fcuntion } fn 防抖被执行函数 
	 *@param { Number }  delay 时间单位内
	 *@return { Fcuntion }    防抖函数
	 */
	debounce(fn, delay) {
		let timer = null
		return function(...args) {
			let context = this
			if (timer) clearTimeout(timer)
			timer = setTimeout(function() {
				fn.apply(context, args)
			}, delay)
		}
	},

```


