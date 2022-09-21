   ## 集合按字段排序 
  ```javascript
	/**
	 * @param { String } name 字段key
	 */
	// a.sort(sortBy("age"));
	sortBy(name) {
		return function(o, p) {
			var a, b;
			if (typeof o === "object" && typeof p === "object" && o && p) {
				a = o[name];
				b = p[name];
				if (a === b) {
					return 0;
				}
				if (typeof a === typeof b) {
					return a < b ? -1 : 1;
				}
				return typeof a < typeof b ? -1 : 1;
			} else {
				throw ("error");
			}
		}
	},
  ```
   ## 集合按字段倒序 
  ```javascript
	/**
	 * @param { String } name  字段key
	 */
	// a.sort(rsortBy("age"));
	rsortBy(name) {
		return function(o, p) {
			var a, b;
			if (typeof o === "object" && typeof p === "object" && o && p) {
				a = o[name];
				b = p[name];
				if (a === b) {
					return 0;
				}
				if (typeof a === typeof b) {
					return a < b ? 1 : -1;
				}
				return typeof a < typeof b ? 1 : -1;
			} else {
				throw ("error");
			}
		}
	},
  ```
