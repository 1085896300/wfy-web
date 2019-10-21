1.将两个字符利用字符串对象的方法变成一个字符,显示在页面id为h1的元素中
答:
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h1 id="h1"></h1>
		<script>
			var h1=document.getElementById('h1');
			var str='1232';
			var str1='5676';
			var nstr=str.concat(str1);
			h1.innerHTML=nstr;
		</script>
	</body>
</html>

2.一个富豪想存87万,给理财顾问写了87w,请自动生成存储870000的方法,显示在页面id为h2的元素中
答:<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h2 id="h2"></h2>
		<script>
			var h2=document.getElementById('h2')
			var str='87';
			var estr=str.padEnd(6,'0');
			h2.innerHTML=estr;
		</script>
	</body>
</html>


3.一个数字79387.348的工程款,保留两位小数存入,显示在页面id为h3的元素中
答:
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h3 id="h3"></h3>
		<script>
			var h3=document.getElementById('h3')
			var str=79387.348;
			var nstr=str.toFixed(2);
			h3.innerHTML=nstr;
		</script>
	</body>
</html>

4.一张图片是一个相对路径img/head/,icon/1.jpg,我只需要拿到它的文件夹目录后显示在页面id为h4的元素中
答:
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h4 id="h4"></h4>
		<script>
			var h4=document.getElementById('h4');
			var img='img/head/,icon/1.jpg';
			var a=img.split(',');
			var b=img[0]+a[1];
			h4.innerHTML=b;
			
		</script>
	</body>
</html>

5.用户输入验证码,无论大小写输入都会正确的方法,显示在页面id为h1的元素中,显示在页面id为h4的元素中
答:<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h4 id="h4"></h4>
		<script>
			var num=prompt('请输入验证码');
			h4.innerHTML=num.toUpperCase();
		</script>
	</body>
</html>
