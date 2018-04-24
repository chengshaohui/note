# HTML

## 表单

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<form action="aa.php" method="post">
		<fieldset>
			<legend>基本信息</legend>
			用户名：<input type="text" placeholder="请输入您的姓名" size="30" maxlength="9" name="user"><br><br>
			密码：<input type="password" placeholder="请输入密码" name="psw"><br><br>
			请上传照片：<input type="file"><br><br>
			<p>请选择您喜欢的音乐：</p>
			<input type="checkbox" checked="checked"> 流行<br>
			<input type="checkbox"> 古典 <br>
			<input type="checkbox"> 爵士 <br>
			<br>
			请选择您的城市：<input type="radio" name="city"> 山西   <input type="radio" name="city"> 北京 <input type="radio" name="city"> 上海
			<br><br>
			请选择你的职位：
			<select name="pos" id="" size="2" multiple="multiple">
				<option value="">全栈工程师</option>	
				<option value="">全栈工程师</option>	
				<option value="">全栈工程师</option>	
				<option value="">全栈工程师</option>	
			</select>
		</fieldset>
		<br>
		<br>
		<br>
		留言：
		<textarea name="" id="" cols="30" rows="10"></textarea>
		<br>
		提交 <input type="submit" value="提交">
		<br>
		按钮 <input type="button" value="按钮">
		重置 <input type="reset" value="重置">
		<input type="color">


		<!-- 年月日 -->
		<br>
		<input type="date"><br>
		<input type="month">
		<input type="week">
		时分 <input type="time">
		年月日时分
		<br><br>
		<input type="datetime-local"><br>
		<br>
		<br>
		<br>
		<br>

		<!-- 范围 -->
		1、数字范围：
		min设置最小值，max设置最大值，step设置步长，value：获取用户操作的值
		<input type="number" min="0" max="10" step="2">
		2、滑块范围<br>
		<input type="range" name="" id="" min="0" max="10" step="2"> <br>
		<!-- 正则验证 -->
		<br>
		email: <input type="email" name="" id="">
		url: <input type="url" name="" id="">
		tel: <input type="tel" name="" id="">
		color： <input type="color" name="" id="">

		<input type="date" name="" id="">
		<input type="month" name="" id="">
		<input type="week" name="" id="">
		<input type="time" name="" id="">
		<input type="datetime-local" name="" id="">
		<br>
		<br>
		<br>
		<br>
		
		number:<input type="number" name="" id="" min="0" max="10" step="2">
		email:<input type="email" name="" id="">
		tel: <input type="tel" name="" id="">
		url: <input type="url" name="" id="">
		color: <input type="color" name="" id="">
		range: <input type="range" name="" id="">

		语义化标签：
		header
		<header>头部</header>
		<nav>导航</nav>
		<main>主体</main>  一般用它写内宽
		<aside>侧导航</aside>  
		<article>文章独立内容</article>
		<footer>底部</footer>
		<section>某一部分</section>

		<hgroup>对标题进行分组
			<h2>2222</h2>
			<h4>44444</h4>
		</hgroup>

		<figure>图像图片的独立内容
			<figcaption>标题</figcaption>
		</figure>
		
		<code>页面中的代码：html</code>
      
		1、进度条<br>
		<progress min="0" max="10" value="8"></progress>
		<br>
		2、范围
		<meter min="0" max="100" value="47"></meter>
		3、音频<br>
		<audio src="over.wav" controls="controls" loop="loop" autoplay="aotuplay"></audio>
		src:文件路径
		controls:向用户显示控件
		loop:循环播放
		autoplay: 页面加载完成后自动播放
		4、视频
		<video src="http://www.imooc.com/video/365" controls="controls" loop="loop" autoplay="autoplay"></video>
		5、画布
		<canvas style="width: 500px;height: 500px; background: #ccc"></canvas>
	</form>
</body>
</html>
```

## 表格

```html
<!-- 表格标签 -->
<!-- cellspacing:设置单元格与但与个之间的距离 -->
<!-- cellpadding：内容与单元格边框之间的距离 -->
<table border="1px" cellspacing="0" cellpadding="10px">
	<!-- 表头 -->
	<thead>
		<!-- 主题 -->
		<caption>WUIF1706班花名</caption>
		<!-- 行 -->
		<tr>
			<!-- th代表加粗的单元格 -->
			<th>姓名</th>
			<th>学号</th>
			<th>练习方式</th>
		</tr>
	</thead>
	<!-- 主体 -->
	<tbody>
		<!-- 行 -->
		<tr>
			<!-- 单元格 -->
			<td>张三</td>
			<td>001</td>
			<td>123456</td>
		</tr>
		<tr>
			<td>张三</td>
			<td>002</td>
			<td>123456</td>
		</tr>
		<tr>
			<td>张三</td>
			<td>003</td>
			<td>123456</td>
		</tr>
	</tbody>
	<!-- 表尾 -->
	<tfoot>
		<!-- 行 -->
		<!-- align:文本的水平居中 -->
		<tr align="center">
			<!-- 单元格 -->
			<td>合计</td>
			<!-- colspan:合并列 -->
			<td colspan="2">43</td>
		</tr>
	</tfoot>
</table>

<table border="1px" cellspacing="0" cellpadding="15px">
    <tr>
        <!-- colspan:合并列 -->
        <td colspan="2"></td>
        <!-- rowspan:合并行 -->
        <td rowspan="2"></td>
    </tr>
    <tr>
        <td rowspan="2"></td>
        <td></td>
    </tr>
    <tr>
        <td colspan="2"></td>
    </tr>
</table>

<!-- align:调整整个表格的水平对齐方式 left  center  right -->
<!-- bgcolor:给表格添加背景色 -->
<!-- width:表格宽度 -->
<!-- height:表格高度 -->
<!-- align:内容水平对齐方式  left  center  right valign:内容垂直对齐方式  top  bottom  middle  baseline -->
<table border="1" cellspacing="0" cellpadding="15" align="center" bgcolor="pink" width="200px" height="200px">
  <!-- height:行的高度 -->
  <tr align="center" valign="baseline" bgcolor="red" height="50px">
      <!-- width：单元格的宽度
      height：单元格的高度 -->
      <td colspan="3" width="100px" height="20px">1</td>
      <td rowspan="3">1</td>
  </tr>
  <tr>
      <td rowspan="3"></td>
      <td></td>
      <td></td>
  </tr>
  <tr>
      <td></td>
      <td></td>
  </tr>
  <tr>
      <td colspan="3"></td>
  </tr>
</table>
```

