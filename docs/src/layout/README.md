   ## 使用grid布局 两列 间隔20px 
  ```html
  <div class="container">
		<div class="item"></div>
		<div class="item"></div>
		<div class="item"></div>
		<div class="item"></div>
		<div class="item"></div>
		<div class="item"></div>
	</div>
	```
	```css
		.container {
			display: grid;
			grid-template-columns: 1fr 1fr;
			grid-gap: 20px;
		}
		.item {
			background-color: red;
			height: 100px;
		}
	```



