### DOM扩展

#### 获取元素

1、document.getElementsByClassName ('class') 通过类名获取元素，以类数组形式存在。

2、document.querySelector('selector') 通过CSS选择器获取元素，符合匹配条件的第1个元素。

3、document.querySelectorAll('selector') 通过CSS选择器获取元素，以类数组形式存在。

#### 类名操作

1、Node.classList.add('class') 添加class

2、Node.classList.remove('class') 移除class

3、Node.classList.toggle('class') 切换class，有则移除，无则添加

4、Node.classList.contains('class') 检测是否存在class

Node指一个有效的DOM节点，是一个通称。

#### 自定义属性

在HTML5中我们可以自定义属性，其格式如下data-*=""，例如

data-info="我是自定义属性"，通过Node.dataset['info'] 我们便可以获取到自定义的属性值。

Node.dataset是以类数组形式存在的

当我们如下格式设置时，则需要以驼峰格式才能正确获取

data-my-name="itcast"，获取Node.dataset['myName']

#### 案例练习

Tab切换

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Tab 标签</title>
    <style>
		body {
			margin: 0;
			padding: 0;
			background-color: #F7F7F7;
		}
	
		.tabs {
			width: 400px;
			margin: 30px auto;
			background-color: #FFF;
			border: 1px solid #C0DCC0;
			box-sizing: border-box;
		}

		.tabs nav {
			height: 40px;
			text-align: center;
			line-height: 40px;
			overflow: hidden;
			background-color: #C0DCC0;
			display: flex;
		}

		nav a {
			display: block;
			width: 100px;
			border-right: 1px solid #FFF;
			color: #000;
			text-decoration: none;
		}

		nav a:last-child {
			border-right: 0 none;
		}

		nav a.active {
			background-color: #9BAF9B;
		}

		.cont {
			overflow: hidden;
			display: none;
		}

		.cont ol {
			line-height: 30px;
		}

    </style>
</head>
<body>
	<div class="tabs">
		<nav>
			<a href="javascript:;" data-cont="local">国内新闻</a>
			<a href="javascript:;" data-cont="global">国际新闻</a>
			<a href="javascript:;" data-cont="sports">体育新闻</a>
			<a href="javascript:;" data-cont="funny">娱乐新闻</a>
		</nav>
		<section class="cont" id="local">
			<ol>
				<li>河感在生矿难，死伤在全10</li>
				<li>禽流感在感在广1处继续蔓延，温家宝指示</li>
				<li>南方大旱，农作物减产绝收面积上亩</li>
				<li>猪流感在广在全国暴发</li>
				<li>禽流感在全国多处继续蔓延，温家宝指示</li>
				<li>南方大旱，农作物减产绝收面积上亩</li>
				<li>猪流感在广东群体性暴发</li>
			</ol>
		</section>
		<section class="cont" id="global">
			<ol>
				<li>河南再次发生矿难，死伤人数超过100</li>
				<li>禽流感次发生蔓延，温家宝指示</li>
				<li>南方大旱，农作物减产绝收面积上亩</li>
				<li>猪流感在广减产绝收发</li>
				<li>禽流感在全国多作物减产绝收面积上亩</li>
				<li>猪流感在广东群体性暴发</li>
			</ol>
		</section>
		<section class="cont" id="sports">
			<ol>
				<li>河南再次发生矿难，死伤人数超过100</li>
				<li>禽流感在全国多处农作物农延，温家宝指示</li>
				<li>南方大旱，农作物减产绝收面积上亩</li>
				<li>猪流感在广东群体性暴发</li>
				<li>禽流感在全农作物继续蔓延，温家宝指示</li>
				<li>南方大农作物减产绝收面积上亩</li>
				<li>猪流感在广东群体性暴发</li>
			</ol>
		</section>
		<section class="cont" id="funny">
			<ol>
				<li>河南再次发生矿难，死伤人数超过100</li>
				<li>禽流感在全国多处农作物农延，温家宝指示</li>
				<li>南方大旱，农作物减产绝收面积上亩</li>
				<li>猪流感在广东群体性暴发</li>
				<li>禽流感在全农作物继续蔓延，温家宝指示</li>
				<li>南方大农作物减产绝收面积上亩</li>
				<li>猪流感在广东群体性暴发</li>
			</ol>
		</section>
    </div>
    <script>
		(function (key) {

			// 获取所有导航
			var navs = document.querySelectorAll('nav a'),
				cont;

			for(var i=0; i<navs.length; i++) {

				// 默认选中
				if(i == key) {
					navs[i].classList.add('active');
					cont = navs[i].dataset['cont'];
					document.querySelector('#' + cont).style.display = 'block';
				}

				navs[i].onclick = function () {
					// 过滤无效点击
					if(this.classList.contains('active')) return;

					var active = document.querySelector('.active');

					active.classList.remove('active');

					cont = active.dataset['cont'];

					document.querySelector('#' + cont).style.display = 'none';

					this.classList.toggle('active');

					cont = this.dataset['cont'];
					
					document.querySelector('#' + cont).style.display = 'block';
				}
			}

		})(3);
	</script>
</body>
</html>
```

#### 其它

1、微数据

http://kayosite.com/html5-microdata.html

可以理解成新语义标签的一种补充

2、ARIA

http://www.zhangxinxu.com/wordpress/2012/03/wai-aria-%E6%97%A0%E9%9A%9C%E7%A2%8D%E9%98%85%E8%AF%BB/#ariaRole
