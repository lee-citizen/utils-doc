   ## 文件链接转Bolb对象
  ```javascript
	/**
	 * @param { String } dataurl 文件链接
	 */
	dataURLtoBlob(dataurl) {
		var arr = dataurl.split(','), mime = arr[0].match(/:(.*?);/)[1],
				bstr = atob(arr[1]), n = bstr.length, u8arr = new Uint8Array(n);
		while (n--) {
				u8arr[n] = bstr.charCodeAt(n);
		}
		return new Blob([u8arr], { type: mime });
	}
  ```
   ## 浏览器下载文件
  ```javascript
	/**
	 * @param { String } url 文件链接
	 * @param { String } filename 文件名
	 */
	downloadFile = (url, filename) => {
		function getBlob (url) {
			return new Promise(resolve => {
				const XML = new XMLHttpRequest();
				XML.open('GET', url, true);
				XML.responseType = 'blob';
				XML.onload = () => {
					if (XML.status === 200) {
						resolve(XML.response);
					}
				};
				XML.send();
			});
		}
		//下载文件
		function saveAs (blob, filename) {
			const elelink = document.createElement("a");
			elelink.style.display = 'none';
			elelink.download = filename;
			elelink.href = window.URL.createObjectURL(blob);
			document.body.appendChild(elelink);
			elelink.click();
			document.body.removeChild(elelink);
		}
		// 调用以上方法进行下载
		getBlob(url).then(blob => {
			saveAs(blob, filename);
		});
	}
  ```
