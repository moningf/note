**标记语法分为单标签和双标签**

# HTML
## HTML基本骨架
```html
<html>
	<head>
		<title>标题</title>
		|
	</head>
	<body>
	|
	</body>
</html>
```


| html  |         整个网页         |
| :---: | :------------------: |
| head  | 网页头部,存放给浏览器看的(如CSS)  |
| body  | 网页主体,存放给用户看的(如图片,文字) |
| title |         网友标题         |



## 标签的关系
作用:
	明确代码的书写位置
	1. 父子关系(嵌套)
	2. 兄弟关系(并列)

## 注释
```html
<!--this is a comment-->
```

## 排版标签

### 标题标签
	标签名:
			h1~h6(双标签)

		eg:
				`<h1>标题1</h1>`

*一般h1只用一次*

### 段落标签
	标签名:
			p(双标签)

	特点:
		1. 独占一行
		2. 段落间存在间隙


## 换行和水平线标签

```html
<br>      #换行
<hr>      #水平线
```

## 文本格式化标签

```html
加粗:
<strong>加粗内容</strong>
<b>加粗内容</b>

倾斜:
<em>倾斜内容</em>
<i>倾斜内容</i>

下划线:
<ins>下划线</ins>
<u>下划线</u>

删除线:
<del>删除线<del>
<s>删除线</s>
```


## 图像标签
单标签:
	`<img src = "图片的URL">`

属性:
	1. alt       替换文本
	2. title     提示文本
	3. width     宽
	4. heigth    高
eg:
`<img src = "URL" alt = "这是一个猫"`
## 超链接标签
`<a href = " ">跳转信息</a>`
当href = "#"时,表示为空,不会跳转

`target = "_blank"`
表示在新窗口打开

## 多媒体标签
### 音频
```html
<audio src = "音频URL"></audio>

常见属性:
src             音频URL
controls        显示音频控制面板
loop            循环播放 
autoplay        自动播放
```

### 视频
```html
<video src = "视频URL"></video>

属性
src
controls
loop
muted      静音播放
autoplay   自动播放(浏览器默认禁用,只有当muted时才能生效)
```

## 列表&表格&表单

### 列表
	作用:
		布局内容排列整齐的区域

分类:
1. 无序列表
2. 有序列表
3. 定义列表

#### 无序列表
标签:ul嵌套li

ul:无序列表
li:列表条目
```html
<ul>
	<li>第一项</li>
	<li>第二项</li>
</ul>
```

#### 有序列表
标签:ol嵌套li
==代码和无序列表相同==


#### 定义列表
标签:dl嵌套dt和dd

dl:定义列表
dt:标题
dd:描述/详情

```html
<dl>
	<dt>标题</dt>
	<dd>列表</dd>
	<dd>列表</dd>
</dl>
```


### 表格
标签: table嵌套tr,tr嵌套td/th

#### 表格基本语法
table   列表
tr      行
th      表头单元格
td      内容单元格

```html
<table>
	<tr>
		<th>姓名</th>
		<th>语文</th>
		<th>数学</th>
		<th>总分</th>
	</tr>
	<tr>
		<th>张三</th>
		<th>99</th>
		<th>100</th>
		<th>199</th>
	</tr>
</table>
```
表格默认没有表格线
在第一行写为`<table border = "1">`会显示表格线


#### 表格结构标签
作用:
	将表格结构划分区域

thead 表格头部
tbody 表格主体
tfoot 表格底部

```html
<table>
	<thead>      #表格头部
		<tr>
			<th>姓名</th>
			<th>语文</th>
			<th>数学</th>
			<th>总分</th>
		</tr>
	</thead>
</table>
```


#### 合并单元格

保留最左最上的单元格,添加属性
1. rowspan   竖直
2. colspan   横向

eg:
	`<th colspan = 1 >例子</th>`


### 表单
	作用:
		收集用户信息

`<input type = "text">`

```
text:文本框(单行)
password:密码框
radio:单选框
		<input type=radio name="age"> 单选框需要同名
checkbox:多选框
		<input type=checkbox checked> 使用checkbox实现默认选中
file:上传文件
		<nput type=file multiple> 使用multiple实现文件多选
```


#### 下拉菜单
标签:
	select嵌套option

```html
<select>
	<option>北京</option>
	<option>上海</option>
	<option selected>广州</option>  #表示默认选中
</select>
```

#### 文本域
作用:
		多行输入文本的控件

标签:textarea ,双标签
	
`<textarea>默认提示文字</textarea>`

#### 标签
作用:
	网页中,某个标签的说明文本

写法:
1.
```html
1.label(标签只包裹内容,不包裹表单控件)
2.设置label标签的for属性和表单控件id属性值相同

<input type="radio" id="man">
<label for="man">男</label>
```
2.
```html
使用label标签直接包裹文字和表单控件,不需要属性
<label><input type="radio">女</label>
```

#### 按钮
`<button type=" ">按钮</button>`

type属性值
1. submit:提交按钮,点击后提交数据到后台(默认)
2. reset:重置按钮,点击后将表单控件恢复为默认值(只有在from标签内才有用)
3. button:普通按钮,无默认功能,一般与javaScript配合使用

管理表单区域 from
```html
<from action=" ">  #action为表单发送数据的地址

</from>
```





### 无语义的布局标签
作用:
	布局网页(划分网页区域,摆放内容)

```html
大盒子
<div>内容</div>

小盒子
<span>内容</span>
```


### 字符实体
作用:
	在网页中显示预留的字符

空格:  &nbsp;
<  :  &lt
\> :  &gt