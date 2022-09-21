


  [👉uniapp官网](https://uniapp.dcloud.net.cn/)
  
  ## 微信登录 
  ``` javascript
  	wxlogin: function() {
		return new Promise((resolve, reject) => { //使用了Promise
			uni.login({
				provider: 'weixin',
				success: function(loginRes) {
					resolve(loginRes)
				},
				fail: function(res) { //错误的时候
					uni.showToast({
						title: "服务器忙，请稍后重试！",
						icon: "none"
					})
					//reject(res); //Promise返回失败
				}
			})
		})
	},
  ```
  ## 根据页面高度判断条数 
  ``` javascript
	getPageSize: function(rowHeight, offsetHeight) {
		var rpxRate = 750 / uni.getSystemInfoSync().windowWidth
		var windowHeightRpx = rpxRate * uni.getSystemInfoSync().windowHeight - (offsetHeight == undefined ? 0 :
			offsetHeight)
		return (Math.floor(windowHeightRpx / rowHeight / 10) + 1) * 10
	},

  ```
  ## 提示框
  ``` javascript
  /**
   * @param { String } title 提示文字
   */
	msg(title) {
		uni.showToast({
			title: title,
			icon: 'none'
		})
	},
  ```
  ## 复制
  ``` javascript
	/**
	 * @param { String } code 复制文字
	 * @param { String } msg 提示文字
	 */
	onCopy(code, msg) {
		uni.setClipboardData({
			data: code,
			success: (data) => {
				uni.showToast({
					title: msg ? msg : '内容已复制',
					icon: 'none'
				})
			},
			fail: function(err) {},
			complete: function(res) {}
		});
	},
  ```
  ## 本地储存(同步)
  ``` javascript
  /**
   * @param { String } keyName 键名
   * @param { any } data 值
  */
	setStorageSync(keyName, data) {
		uni.setStorageSync(keyName, data);
	},
  ```
  ## 路由跳转
  ``` javascript
  /**
   * @param { String } url  
   */
	navTo(url) {
		uni.navigateTo({
			url: url
		});
	},
  ```
  ## 路由后退
  ``` javascript
	back() {
		uni.navigateBack({
			delta: 1
		});
	},
  ```
  ## 图片处理-预览图片
  ``` javascript
	/**
	 * @param { Array } urls - 图片列表
	 * @param { Number } current - 首个预览下标
	 */
	previewImage(urls = [], current = 0) {
		uni.previewImage({
			urls: urls,
			current: current,
			indicator: 'default',
			loop: true,
			fail(err) {
				console.log('previewImage出错', urls, err)
			},
		})
	},
  ```
  ## 打电话
  ``` javascript
	/**
	 * @param { String<Number> } phoneNumber - 数字字符串
	 */
	callPhone(phoneNumber = '') {
		let num = phoneNumber.toString()
		uni.makePhoneCall({
			phoneNumber: num,
			fail(err) {
				console.log('makePhoneCall出错', err)
			},
		});
	},
  ```





<!-- ## 效果浏览
<!-- * [Github Pages](https://missfoxw.github.io/docsify-template/) -->

<!-- ## 参考 -->

<!-- * [👉docsify](https://docsify.js.org/#/) -->
<!-- * [👉docsify-themeable](https://jhildenbiddle.github.io/docsify-themeable/#/) --> 
