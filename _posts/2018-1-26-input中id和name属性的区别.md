---
layout:     post
title:      input中id和name属性的区别
subtitle:   
date:       2018-1-26
author:     WHY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - html
---

# input中id和name属性的区别

做网站很久了，但到现在还没有搞明白input中name和id的区别，最近学习jquery，又遇到这个问题，就在网上搜集资料。看到这篇，就整理出来，以备后用。

可 以说几乎每个做过Web开发的人都问过，到底元素的ID和Name有什么区别阿？为什么有了ID还要有Name呢?! 而同样我们也可以得到最classical的答案：ID就像是一个人的身份证号码，而Name就像是他的名字，ID显然是唯一的，而Name是可以重复 的。

上周我也遇到了ID和Name的问题，在页面里输入了一个input type=“hidden”，只写了一个ID=‘SliceInfo’，赋值后submit，在后台用 Request.Params[“SliceInfo”]却怎么也去不到值。后来恍然大悟因该用Name来标示，于是在input里加了个 Name=‘SliceInfo’，就一切ok了。

第一段里对于ID和Name的解答说的太笼统了，当然那个解释对于ID来说是完全对的，它就是Client端HTML元素的Identity。而Name其实要复杂的多，因为Name有很多种的用途，所以它并不能完全由ID来代替，从而将其取消掉。具体用途有：

用途1: 作为可与服务器交互数据的HTML元素的服务器端的标示，比如input、select、textarea、和button等。我们可以在服务器端根据其Name通过Request.Params取得元素提交的值。
用途2: HTML元素Input type='radio’分组，我们知道radio button控件在同一个分组类，check操作是mutex的，同一时间只能选中一个radio，这个分组就是根据相同的Name属性来实现的。
用 途3: 建立页面中的锚点，我们知道link是获得一个页面超级链接，如果不用href属性，而改用Name，如：，我们就获得了一个页面锚点。
用途4: 作为对象的Identity，如Applet、Object、Embed等元素。比如在Applet对象实例中，我们将使用其Name来引用该对象。
用途5: 在IMG元素和MAP元素之间关联的时候，如果要定义IMG的热点区域，需要使用其属性usemap，使usemap="#name"(被关联的MAP元素的Name)。
用 途6: 某些特定元素的属性，如attribute，meta和param。例如为Object定义参数或Meta中。

显然这些用途都不是能简单的使用ID来代替掉的，所以HTML元素的ID和Name的却别并不是身份证号码和姓名这样的区别，它们更本就是不同作用的东西。

当 然HTML元素的Name属性在页面中也可以起那么一点ID的作用，因为在DHTML对象树中，我们可以使用 document.getElementsByName来获取一个包含页面中所有指定Name元素的对象数组。Name属性还有一个问题，当我们动态创建 可包含Name属性的元素时，不能简单的使用赋值element.name = "…"来添加其Name，而必须在创建Element时，使用document.createElement(’’)为元素添加Name属性。这是什么意思啊？看下面的例子就明白了。

消息框里显示的结果是：。

消息框里显示的结果是：。
初始化Name属性的这个设计不是IE的缺陷，因为MSDN里说了要这么做的，可是这样设计的原理什么呢？我暂时没有想太明白。

这 里再顺便说一下，要是页面中有n(n>1)个HTML元素的ID都相同了怎么办？在DHTML对象中怎么引用他们呢？如果我们使用ASPX页面，这 样的情况是不容易发生的，因为aspnet进程在处理aspx页面时根本就不允许有ID非唯一，这是页面会被抛出异常而不能被正常的render。要是不 是动态页面，我们硬要让ID重复那IE怎么搞呢？这个时候我们还是可以继续使用document.getElementById获取对象，只不过我们只能 获取ID重复的那些对象中在HTML Render时第一个出现的对象。而这时重复的ID会在引用时自动变成一个数组，ID重复的元素按Render的顺序依次存在于数组中。

表单元素(form input textarea select)与框架元素(iframe frame)用 name
这些元素都与表单(框架元素作用于form的target)提交有关, 在表单的接收页面只
接收有name的元素, 赋ID的元素通过表单是接收不到值的, 你自己可以验证一下.
有一个例外: A 可以赋 name 作为锚点, 也可以赋ID

当然上述元素也可以赋ID值, 赋ID值的时候引用这些元素的方法就要变一下了.
赋 name: document.formName.inputName document.frames(“frameName”)
赋 ID : document.getElementById(“inputID”) document.all.frameID

只能赋ID不能赋name的元素:(除去与表单相关的元素都只能赋ID)

body li table tr td th p div span pre dl dt dd font b 等等

