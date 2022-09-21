   ## 对象转url参数形式 
  ```javascript
	/**
	 * @param { Object } obj
	 * @return { String }
	 */
	objToUrlParams(obj) {
		var result = []
		for (let key in obj) {
			result.push(key + '=' + obj[key])
		}
		return result.join("&")
	},
  ```
   ## 对比两个对象是否相同
  ```javascript
	/**
	 * @param { Object } a 对象a
	 * @param { Object } b 对象b
	 */
	isObjEqual(a, b) {
		let aProps = Object.getOwnPropertyNames(a);
		let bProps = Object.getOwnPropertyNames(b);
		let flag = true;
		if (aProps.length !== bProps.length) return false;
		for (let i in a) {
			if (a[i] !== b[i]) {
				if (typeof(a[i]) === 'object') {
					if (!compareParams(a[i], b[i])) {
						flag = false;
						break;
					}
				} else {
					flag = false;
					break;
				}
			}
		}
		return flag;
	},
  ```
   ## 填充对象
  ```javascript
	/**
	 * @param { Object } sourse 源对象
	 * @param { Object } target 目标对象
	 */
	mapTo(sourse, target) {
		if (!sourse) return target
		for (var key in target) {
			if (sourse.hasOwnProperty(key) === true) {
				//此处hasOwnProperty是判断自有属性，使用 for in 循环遍历对象的属性时，原型链上的所有属性都将被访问会避免原型对象扩展带来的干扰
				target[key] = sourse[key];
			}
		}
		return target;
	},
  ```