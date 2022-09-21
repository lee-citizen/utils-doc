  ## url参数转为对象 
  ``` javascript
	/**
	 * @param { String } url
	 * @return { Object }
	 */
	 urlToToObj(url){
		const obj = {};
		if (url) {
		  const params = url.split('?')[1].split('&');
		  params.map(item => obj[item.split("=")[0]] = item.split("=")[1]);
		}
		return obj;
		// {abc: '1', type: '2'}
	  },
  ```
  ## 验证手机号 
  ``` javascript
	/**
	 * @param { String } phone
	 * @return { Boolean }
	 */
	checkPhone: function(phone) {
		if (!(/^1(1|2|3|4|5|6|7|8|9)\d{9}$/.test(phone))) {
			return false;
		}
		return true;
	},
  ```
  ## 隐藏手机号中间四位 
  ``` javascript
	/**
	 * @param { String } phone
	 * @return { String }
	 */
	hidePhone: function(phone) {
		let reg = /^(\d{3})\d{4}(\d{4})$/;
		let res = phone.replace(reg, '$1****$2');
		return res;
	},
  ```
  ## 身份证验证 
  ``` javascript
	/**
	 * @param { String } val 身份证号
	 */
	cerCode: function(val) {
		var idcard = val;
		var regex1 =
			/^[1-9][0-7]\d{4}((([0-9]{3}[1-9]|[0-9]{2}[1-9][0-9]{1}|[0-9]{1}[1-9][0-9]{2}|[1-9][0-9]{3})(((0[13578]|1[02])(0[1-9]|[12][0-9]|3[01]))|((0[469]|11)(0[1-9]|[12][0-9]|30))|(02(0[1-9]|[1][0-9]|2[0-8]))))|((([0-9]{2})(0[48]|[2468][048]|[13579][26])|((0[48]|[2468][048]|[3579][26])00))0229))\d{3}(\d|X|x)?$/;

		switch (idcard.length) {
			case 15:
				if ((parseInt(idcard.substr(6, 2)) + 1900) % 4 == 0 ||
					((parseInt(idcard.substr(6, 2)) + 1900) % 100 == 0 && (parseInt(idcard
						.substr(6, 2)) + 1900) % 4 == 0)) {
					var regex2 =
						/^[1-9][0-9]{5}[0-9]{2}((01|03|05|07|08|10|12)(0[1-9]|[1-2][0-9]|3[0-1])|(04|06|09|11)(0[1-9]|[1-2][0-9]|30)|02(0[1-9]|[1-2][0-9]))[0-9]{3}$/; // 测试出生日期的合法性
				} else {
					var regex2 =
						/^[1-9][0-9]{5}[0-9]{2}((01|03|05|07|08|10|12)(0[1-9]|[1-2][0-9]|3[0-1])|(04|06|09|11)(0[1-9]|[1-2][0-9]|30)|02(0[1-9]|1[0-9]|2[0-8]))[0-9]{3}$/; // 测试出生日期的合法性
				}

				if (regex2.test(idcard))
					return true;
				else {
					return false;
				}
				break;
			case 18:
				if (regex1.test(idcard)) {
					idcard = idcard.split("");
					var S = (parseInt(idcard[0]) + parseInt(idcard[10])) * 7 +
						(parseInt(idcard[1]) + parseInt(idcard[11])) * 9 +
						(parseInt(idcard[2]) + parseInt(idcard[12])) * 10 +
						(parseInt(idcard[3]) + parseInt(idcard[13])) * 5 +
						(parseInt(idcard[4]) + parseInt(idcard[14])) * 8 +
						(parseInt(idcard[5]) + parseInt(idcard[15])) * 4 +
						(parseInt(idcard[6]) + parseInt(idcard[16])) * 2 +
						parseInt(idcard[7]) * 1 + parseInt(idcard[8]) * 6 +
						parseInt(idcard[9]) * 3;
					var Y = S % 11;
					var M = "F";
					var JYM = "10X98765432";
					M = JYM.substr(Y, 1);
					/* 判断校验位 */
					if (M == idcard[17].toUpperCase()) {
						return true;
					} else {
						return false;
					}
				} else {
					return false;
				}
				break;
			default:
				return false;
		}
	},
  ```
   ## 长度不够自动补0 
  ```javascript
  /**
	 * @param { Number } num 处理的数字
	 * @param { Number } length 长度
	 */
	prefixInteger: function(num, length) {
		return (num / Math.pow(10, length)).toFixed(length).substr(2);
	},
  
  ```
   ## 长度过滤超出省略 
  ```javascript
	/**
	 *@param { String } str 操作的字符串 
	 *@param { Number } end 长度 default:5
	 *@param { Number } start 起始下标  default:0
	 */
	filterLength(str, end = 5, start = 0) {
		if (!str) return "";
		str = String(str)
		return str.length > end ? str.substr(start, end) + "..." : str
	},
  
  ```
   ## 生成随机字符串 
  ```javascript
	/**
	 *@param { String } len 生成字符串的长度 
	 */
	randomStr(len) {
		len = len || 32;
		var chars = 'ABCDEFGHJKMNPQRSTWXYZabcdefhijkmnprstwxyz123456789';
		var maxPos = chars.length;
		var pwd = '';
		for (let i = 0; i < len; i++) {
			pwd += chars.charAt(Math.floor(Math.random() * maxPos));
		}
		return pwd;
	},
  
  ```
   ## 指定信息加密 
  ```javascript
	/**
	 *@param { String } str 操作的字符串
	 *@param { Number } start 起始位置 default:0
	 *@param { Number } end   结束位置 default:-1
	 */
	encryption(str, start = 0, end = -1) {
		let result = str.replace(str.slice(Number(start), Number(end)), (a) => {
			let ni = "*";
			return ni.repeat(a.length);
		})
		return result;
	},
  
  ```
   ## 判断字符串是否JSON 
  ```javascript
  /**
  * @param { String } str 字符串
  * @return { Boolean }
  */
	isJSON (str){
		if (typeof str == 'string') {
			try {
				var obj=JSON.parse(str);
				if(typeof obj == 'object' && obj ){
					return true;
				}else{
					return false;
				}
			} catch(e) {
				console.log('error：'+str+'!!!'+e);
				return false;
			}
		}
	},
  
  ```
   ## 判断是否数字 
  ```javascript
	/**
	 * @param { String<Number> } checkVal 检查的值
	 */
	isNumber (checkVal){
		var reg = /^-?[1-9][0-9]?.?[0-9]*$/;
		return reg.test(checkVal);
	}
  
  ```

  
