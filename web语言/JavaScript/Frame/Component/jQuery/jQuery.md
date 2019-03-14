## jQuery的优势

1. 轻量级
2. 强大的选择器
3. 出色的DOM操作的封装
4. 可靠的事件处理机制
5. 完善的Ajax
6. 不污染顶级变量
7. 出色的浏览器兼容性
8. 链式操作方式
9. 隐式迭代
10. 行为层与结构层的分离
11. 丰富的插件支持
12. 完善的文档
13. 开源



## `## 说明

1. `$ = jQuery`
2. `$(); = jQuery();`
3. `$("选择器");` //获得jQuery对象
4. `$("选择器","标记|jQuery对象");` //获得jQuery对象
5. `$("<标记><标记></标记></标记>");`
6. `$("<标记/>",{属性:值,属性:值,属性:值})`



## jQuery选择器的优势

1. 简洁的书写方式

   Example

   ```js
   $('#id')代替document.getElementById()函数
   ```

2. 支持CSS1到CSS3选择器

   >  css需要考虑浏览器的支持，jquery不需要考虑

3. 完善的处理机制



## jQuery选择器

1. 基本选择器

	`$("*")`
	`$("#id")`
	`$(".class")`
	`$("span")`
	`$("#id,span,.class")`

2. 层次选择器

	

​		 $("选择器1 选择器2")	从匹配选择器1的后代元素中选取匹配选择器2的元素						集合元素	​$("div span")					选取div里的所有span元素
​		 $("选择器1>选择器2")	从匹配选择器1的子元素中选取匹配选择器2的元素						集合元素	​$("div>span")					选取div元素下元素名称为span的子元素
​		 $('选择器1+选择器2')	从匹配选择器1后面的第一个兄弟元素中选取匹配选择器2的元素	集合元素	​$(".one+div")					选取class为one的下一个div兄弟元素
​		 $('选择器1~选择器2')	从匹配选择器1后面的所有兄弟元素中选取匹配选择器2的元素		集合元素	​$("#two~div")					选取id为two的元素后面的所有div元素
​	 3、过滤选择器
​		 1、基本内容过滤器
​			 :first						选取第一个元素																			单个元素	$("div:first")						选取div中第一个元素
​			 :last							选取最后一个元素																			单个元素	​$("div:last")						选取div中最后一个元素
​			 :not(selector)			取出所有与给定选择器不匹配元素													集合元素	$("input:not(.myclass)")	选取class不没有class的input元素
​			 :even						选取索引是偶数的所有元素，索引从0开始									集合元素	​$("input:even")				选取索引是偶数的input元素
​			 :odd						选取索引是奇数的所有元素，索引从0开始									集合元素	$("input:odd")					选取索引是奇数的input元素
​			 :eq(index)				选取索引等于index的元素，index从0开始									单个元素	​$("input:eq(1)")				选取索引是1的input元素
​			 :gt(index)				选取索引大于index的元素，index从0开始									集合元素	$("input:gt(1)")				选取索引大于1的input元素
​			 :lt(index)					选取索小于index的元素，index从0开始										集合元素	​$("input:lt(1)")					选取索引小于1的input元素
​			 :header					选取所有标题元素，如：h1,h2,h3等												集合元素	$(":header")					选取网页中所有<h1><h2>
​			 :focus  1.6+			选择获得焦点的元素																		单个元素	​$(":focus")						选取获得焦点的元素
​			 :animated				选取当前正在实行动画的所有元素													集合元素	$("div:animated")			选取正在执行动画的div元素
​		 2、内容过滤器
​			 :contains(text)		选取含有文本内容为“text”的元素												集合元素	​$("div:contains('我')")		选取还有文本“我”的div元素
​			 :empty					选取不包含后代元素和文本的空元素												集合元素	$("div:empty")					选取不包含子元素的div的空元素
​			 :has(selector)			选取含有后代元素并匹配选择器的元素											集合元素	​$("div:has(p)")					选取含有p元素的div元素
​			 :parent					选取后代元素或文本的非空元素													集合元素	$("div:parent")				选取拥有子元素的div元素
​		 3、可见性过滤器
​			 :hidden	  				选取所有不可见元素																		集合元素
​			 :visible					选取所有可见的元素																		集合元素
​		 4、属性过滤器
​			 [attribute]										选取拥有此属性的元素																									集合元素	​$("div[id]")						选择拥有属性id的元素
​			 [attribute=value]							选取属性的值为value																									集合元素	$("div[title=test]")			选取属性title为“test”的<div>元素
​			 [attribute!=value]							选取属性的值不等于value的元素																					集合元素	​$("div[title!=test]")			选取属性title不等于“test”的div元素（没有属性title的div也会选取）
​			 [attribute^=value]							选取属性的值为value开始的元素																					集合元素	$("div[title^=test]")		选取属性title以“test”开始的div元素
​			 [attribute​$=value]							选取属性的值以value结束的元素																					集合元素	$("div[title​$=test]")			选取属性title以“test”结束的div元素
​			 [attribute*=value]							选取属性的值含有value的元素																						集合元素	$("div[title*=test]")			选取属性title含有“test” 的div元素
​			 [selector1][selector2][selectorn]	用属性选择器合并成一个符合属性选择器，满足多个条件。每选择一次，缩小一次范围	集合元素	$("div[id][title​$=test]")	选取拥有属性id并且title以“test”开始的div元素
​		 5、子元素过滤器（从1开始计数）
​		 :nth-child(index/even/odd/equation)
​			 选取每个匹配元素下的第index个子元素或者奇偶元素（index从1算）													集合元素
​		 :first-child
​			 选取每个父元素的第一个子元素																											集合元素
​		 :last-child
​			 选取每个父元素的最后一个子元素																										集合元素
​		 :only-child
​			 如果某个元素是它父元素中唯一的子元素，那么将会被匹配。如果父元素中还有其他元素，则不匹配	集合元素
​	 4、表单选择器
​		 :input			选取所有的input 、textarea、select和button	集合元素	$(":input")			选取所有input textarea、select 和button元素
​		 :text			选取所有的单行文本框										集合元素	​$(":text")				选取所有的单行文本框
​		 :password	选取所有的密码框												集合元素	$(":password")	选取所有的密码框
​		 :radio			选取所有的单选框												集合元素	​$(":radio")			选取所有的单选框
​		 :checkbox	选取所有的复选框												集合元素	$(":checkbox")	选取所有的复选框
​		 :submit		选取所有的提交按钮											集合元素	​$(":submit")			选取所有的提交按钮
​		 :image		选取所有的图像按钮											集合元素	$(":image")			选取所有的图像按钮
​		 :reset			选取所有的重置按钮											集合元素	​$(":reset")			选取所有的重置按钮
​		 :button		选取所有的按钮												集合元素	$("button")			选取所有的按钮
​		 :file				选取所有的上传文件											集合元素	​$("file")				选取所有的上传文件
​		 :hidden		选取所有不可见元素											集合元素	$(":hidden")		选取所有不可见元素（已经在不可见性过滤选择器中讲过）

链式操作方式 
	 链式操作概述:生成一个jQurey对象后，既要对它进行一次或多次的普通操作，同时还要对它进行更改操作。于是有必要把生成的jQuery对象存储在一个变量中，满足多次调用的需要

更改jQuery对象的方法
	 1、更改为后代元素的集合
		 1、children()方法：是用来选择子元素的
			 children("选择器")		//选择子元素中，所有匹配选择器的直接子元素
			 children()					//选择父元素的所有直接子元素
		 2、find()方法：是用来选择后代元素的
			 find("选择器")				//选择后代元素中，所有匹配选择器的后代元素
			 find()							//不选择原先元素任何后代元素
		 3、contents()					//选择匹配元素文本块（节点）和子(不包括孙子等)节点
             说明包括空文本节点
	 2、更改祖先元素的集合
		 1、parent()方法：选择父元素
			 parent("选择器")		//选择父元素中，所有匹配选择器的元素
			 parent()						//选择所有父元素
		 2、parents()方法：选择祖先元素
			 parents("选择器")		//选择祖先元素中，所有匹配选择器的元素
			 parents()					//选择所有祖先元素
		 3、parentsUntil()方法：祖先元素
			 parentsUntil("选择器")//选择祖先元素，直到找到匹配选择器的元素，但不包括匹配元素
			 parentsUntil()				//选择所有祖先元素
		 4.offsetParent()				//选择最近的祖先定位元素，且该元素的CSS属性display不能为none.所谓定位元素是指其CSS属性position取值为relative、absolute或fixed。如果祖先元素中没有合适的元素，则会选择<html>根元素元素
		 5.closest("选择器")			//选择本身和其祖先元素所有匹配选择器的元素。也就是说，先看看原先的元素是否匹配，否则会一层一层地向上找到最先匹配祖先元素。如果祖先没有匹配的返回一个空数组
	 3、更改为兄弟元素集合
		 1、next()和prev()方法
			 next("选择器")			//在原先元素后面的第一个兄弟元素中，选取匹配选择器的元素。next()或next("*")，会选取原先元素后面的第一个兄弟。
			 prev("选择器")			//在原先元素前面的第一个兄弟元素中，选取匹配选择器的元素。prev()或prev("*")，会选取原先元素前面的第一个兄弟。
		 2、nextAll()、prevAll()和siblings()方法
			 nextAll("选择器")		//在原先元素后面的兄弟元素中，选取匹配选择器的元素。nextAll()或nextAll("*")，会选取原先元素后面的所有兄弟。
			 prevAll("选择器")		//在原先元素前面的兄弟元素中，选取匹配选择器的元素。prevAll()或prevAll("*")，会选取原先元素前面的所有兄弟。
			 siblings("选择器")		//在原先元素所有兄弟元素中，选取匹配选择器的元素。siblings()或siblings("*")，会选取原先元素所有兄弟。
	 4、更改为更多元素集合
		 1、add("选择器")			//在原先元素的基础上添加选取匹配选择器的元素
			 说明:$("选择器1").add("选择器2")选取的元素等同于$("选择器1","选择器2"); 
			 --add(参数)
             --参数可以是表达式:"#li1"
             --参数可以是DOM对象:document.getElementById("#li1")
             --参数可以是jQuery对象:$("#li1")
		 2、andSelf()					//加入之前所选的元素，加入当前元素中

jQuery筛选器
	 1、eq(index)						//选择元素中索引值等于index的元素，正向从0开始，逆向从-1开始-2 -3等
	 2、first()								//选择匹配元素中第一个，等于eq(0);
	 3、last()								//选择匹配元素中最后一个,等于eq(-1);
	 2、slice(start,[end])			//筛选索引从start到(end-1)的元素。	例如:slice(2,5);指得是从索引为2到5之前，也就是2、3、4元素
	 3、filter("选择器")				//选择匹配选择器的元素
	 4、not("选择器")				//选择不匹配选择器的元素
	 5、has("选择器")				//选择匹配选择器的后代元素

还原jQuery对象的方法
	 end()									//返回上一个选择器，可连续使用

jQuery对象的文档处理
	 1、移动元素
		 1、append()					//向每个匹配的元素内部追加内容。例如:$("选择器  1").append("选择器2");会将匹配选择器2的元素，移动到匹配选择器1的内部尾部。
			 例:  $("div").append($("p")).addClass("highlight");
		 2、appendTo()				//将所有匹配的元素追加到指定的元素中
			 //jQuery对象会发生改变，更改为匹配$(“p”)元素
			 appendTo()和append()方法颠倒过来
			 例：$("p").appendTo($("div")).addClass("highlight");//功能同上
		 3、prepend()					//向每个匹配的元素内部前置内容
		 4、prependTo()				//将所有匹配的元素前置倒指定的元素中
		 5、after()						//在每个匹配的元素之后插入内容
		 6、insertAfter()				//将所有匹配的元素插入到指定元素的后面
		 7、before()					//在每个匹配的元素之前插入内容
		 8、insertBefore()			//将所有匹配的元素插入到指定的元素的前面
	 2、添加元素
		 1、创建生成jQuery对象
			 例如：$("<p>p1</p>").appendTo($("div")).addClass("highlight");
		 2、复制生成jQuery对象
			 使用clone方法，可以复制当前匹配的页面元素。
	 3、替换元素
		 1、replaceWith()			//可以移动页面上的原有的元素来替换当前选定的页面所有匹配元素
			 例如：
				 $(function(){
					 $("p").replaceWith("<strong>火哥火火的</strong>");
					 // 同样的实现： $("<strong>你最不喜欢的水果是?</strong>").replaceAll("p");
				 });
		 2、relpaceAll()				//是replaceWith()颠倒过来。
	 4、包裹元素	//包裹节点，就是将某个节点用其他标记包裹起来
		 1、wrapall()					//该方法将所有匹配的元素用一个元素包裹起来
			 例如：$("strong").wrapall("<b></b>");是将所有的strong标记外加上了b标记
		 2、wraplnner()				//改方法是将每一个匹配的元素的子内容（包括文本节点）用其他结构化得标记包裹起来。
			 例如：$("strong").wrapinnerl("<b></b>");可以换成这样的代码：<strong><b>你好</b></strong>，b加到strong的里面
	 5、删除和清空元素
		 1、remove()					//所有匹配的元素删除
			 例如：$("ul li:eq(1)").remove();
			 根据属性删除：$("ul li").remove("li[title!="ab"]");
		 2、empty()						//清除节点，它能清除元素中的所有后代节点
			 $("ul li:eq(1)").empty();//回去第2个li元素节点后，清此元素里的内容。

jQuery对象属性处理
	 1、元素属性处理
		 1、attr()							//获取元素某个属性的取值。$("选择器").attr(name)获得匹配选择器的对象的指定属性。$("选择器").attr(name,value)设置匹配选择器的对象的指定属性
		 2、removeAttr()			//删除某个属性的取值
	 2、元素的class属性处理
		 1、addClass()					//元素添加一个class名
		 2、removeClass()			//元素移除一个或多个属性值
		 3、toggleClass()			//切换class属性中的一个或多个属性值的切换
		 4、hasClass()					//判断匹配元素class属性中是否含有某个值，有返回true，没有返回false;
	 3、元素内部的HTML，文本处理
		 1、html()						//可以用来读取或者设置某个元素中的HTML内容（包括标记）
		 2、text()							//用来读取或者设置某个元素中的文本内容
	 4、表单的属性处理
		 1、val()							//获得或设置匹配选择器的表单元素的value值
		 2、checked、 selected属性，选中为true，否则为false;

jQuery对象的css处理
	 1、css基本属性的处理
		 css()								//获取CSS属性值。$(“选择器”).css(name);获取匹配选择器的元素指定CSS属性的值
	 2、css的尺寸属性处理
		 1、height()						//获取或设置CSS属性height的值，单位是像素
		 2、width()						//获取或设置CSS属性width的值，单位是像素
		 3、innerHeight()			//用户获得或设置元素的实际高度值，包括padding+width不包括border
		 4、innerWidth()				//用户获得或设置元素的实际宽度值，包括padding+width不包括border
		 5、outerHeight()			//用户获得或设置元素的实际高度值，包括padding+border+width+margin
		 6、outterWidth()			//用户获得或设置元素的实际宽度值，包括padding+border+width+margin
	 3、css的位置属性处理
		 1、offset()						//获取或设置当前元素的相对窗口偏移量
		 2、position()					//获取或设置当前元素相对于父元素的偏移量
		 3、scrollTop()				//获取或设置竖向滚动条的位置
		 4、scrollLeft()					//获取或设置横向滚动条的位置