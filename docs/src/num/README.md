## 将数字处理成万返回
```javascript
	/**
	 *@param { Number } num 数字
	 */
	dealCount(num) {
		if (num > 10000) {
			return Math.floor(num / 100) / 100 + "w"
		}
		return num;
	},
```