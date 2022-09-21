  ## 格式化音频时间 
  ``` javascript
	/**
	* @param { Number | String } s 秒
	*/
	formatAudioDuration(s) {
		console.log(s)
		if (s == 0 || s.length == 0) return "";
		s = parseInt(s)
		var m = (s / 60) //分
		var timeStr = ""
		if (m < 1) {
			timeStr = s + "″"
		} else {
			if (s % 60 == 0) {
				timeStr = parseInt(m) + "′"
			} else {
				timeStr = parseInt(m) + "′" + (s - parseInt(m) * 60) + "″"
			}
		}
		return timeStr;
	},
  ```

  ## 天时分秒 
  ``` javascript
	/**
	* @param { Number | String } s 秒
	* @return {d: '00', h: '00', m: '01', s: '00'}
	*/
	format(s) {
		let format = {
			d: '00',
			h: '00',
			m: '00',
			s: '00',
		}
		if (t > 0) {
			let d = Math.floor(t / 86400)
			let h = Math.floor((t / 3600) % 24)
			let m = Math.floor((t / 60) % 60)
			let s = Math.floor(t % 60)
			format.d = d < 10 ? '0' + d : d
			format.h = h < 10 ? '0' + h : h
			format.m = m < 10 ? '0' + m : m
			format.s = s < 10 ? '0' + s : s
		}
		return format
	},
  ```

  ##  日期格式化
  ``` javascript
	/**
	 * @param {( Object | String | Number )} time 
	 * @return {d: '00', h: '00', m: '01', s: '00'}
	 */
	parseTime(time, cFormat) {
		if (arguments.length === 0 || !time) {
			return null
		}
		const format = cFormat || '{y}-{m}-{d} {h}:{i}:{s}'
		let date
		if (typeof time === 'object') {
			date = time
		} else {
			if ((typeof time === 'string')) {
				if ((/^[0-9]+$/.test(time))) {
					// support "1548221490638"
					time = parseInt(time)
				} else {
					// support safari
					// https://stackoverflow.com/questions/4310953/invalid-date-in-safari
					time = time.replace(new RegExp(/-/gm), '/')
				}
			}

			if ((typeof time === 'number') && (time.toString().length === 10)) {
				time = time * 1000
			}
			date = new Date(time)
		}
		const formatObj = {
			y: date.getFullYear(),
			m: date.getMonth() + 1,
			d: date.getDate(),
			h: date.getHours(),
			i: date.getMinutes(),
			s: date.getSeconds(),
			a: date.getDay()
		}
		const time_str = format.replace(/{([ymdhisa])+}/g, (result, key) => {
			const value = formatObj[key]
			// Note: getDay() returns 0 on Sunday
			if (key === 'a') { return ['日', '一', '二', '三', '四', '五', '六'][value ] }
			return value.toString().padStart(2, '0')
		})
		return time_str
	}
		```

## *分钟前
```javascript
	/**
	 * @param { Number } time
	 * @param { String } option
	 * @returns { String }
	 */
	formatTime(time, option) {
		debugger;
		if (('' + time).length === 10) {
			time = parseInt(time) * 1000
		} else {
			time = +time
		}
		const d = new Date(time)
		const now = Date.now()

		const diff = (now - d) / 1000

		if (diff < 30) {
			return '刚刚'
		} else if (diff < 3600) {
			// less 1 hour
			return Math.ceil(diff / 60) + '分钟前'
		} else if (diff < 3600 * 24) {
			return Math.ceil(diff / 3600) + '小时前'
		} else if (diff < 3600 * 24 * 2) {
			return '1天前'
		}
		if (option) {
			return parseTime(time, option)
		} else {
			return (
				d.getMonth() +
				1 +
				'月' +
				d.getDate() +
				'日' +
				d.getHours() +
				'时' +
				d.getMinutes() +
				'分'
			)
		}
	}
```

