#第六章 DOM
###6.1DOM概述
####6.1.1 DOM的概念
DOM文档对象模型，DOM对象不仅仅是一个普通的内置对象，他还是一个巨大的API的核心对像，他讲文档的内容呈现在js面前，并赋予了js操作文档的能力。

####6.1.2 DOM和JavaScript的关系
一个web页面是一个文档，这个文档可以在浏览器窗口或者作为html源代码显示出来，但上述两个情况都是同一个文档，DOM提供了对一份文档的另一种表现，存储和操作的方式，DOM能够使用JavaScript脚本语言进行修改。

####6.1.3 DOM节点
加载HTML页面时，web浏览器生成一个树形结构，用来表示页面的内部结构，DOM将这种结构理解为节点组成，根据W3c的html DOM标准，html文档找那个所有的内容都是节点
>整个文档是一个文档节点
>每个html元素是元素节点
>html元素内的文本是文本节点（空格也算）
>每个html属性都是属性节点（id）
>注释也是节点，叫注释节点

####6.1.4 DOM树
DOM树体现着html页面的层级结构，而DOM树有DOM文档和DOM元素树两种。DOM元素树包含的只有元素节点，而DOM文档树则包括DOM文档中的所有内容。

###6.2获取元素
####6.2.1 getElementById
document.getElementById('')的方法，接收一个参数，获取元素的id，如果找到相应元素，则返回该元素的，否则返回null

      //用变量接住 在文档中 找元素 用id "d"
       var d=document.getElementById('d');

####6.2.2 用标签名获取元素
document.getElementsByTagName（）可以获取钙元素名称下所有的元素，返回一个伪数组，或者说是一个节点列表

         var lis=document.getElementsByTagName('li');
         //伪数组
         console.log(lis);

在某一个元素中，并不是在全局文档中利用标签获取元素，这样更加精准

         var ul=document.getElementById('ul');
         var list=document.getElementsByTagName('li');
         console.log(list);

当元素只有一个的时候,返回的也依然是一个列表,而不是一个元素.可以通过数组的下标找到该元素.

        var div = document.getElementsByTagName('div');
        console.log(div[0]);

####6.2.3 类名获取元素
     
        var a=document.getElementsByClassName('a');
        console.log(a);

####6.2.4 用选择器获取元素
querySelector()和querySelectorAll()可以依靠选择器找到元素,但是前者只能找到元素列表的第一个元素,而后者可以全部找到.注意,该方法性能没有直接利用标签寻找高.

        var ul = document.getElementById('ul')
        var x = document.querySelector('#div>div a');
        var lis = ul.querySelectorAll('li');
        console.log(lis);

        var a=document.querySelector('.a');
        console.log(a);


#####6.2.5 用name属性值获取元素
getElementsByName()方法可以获取相同名称的name元素,返回一个伪数组对象.

        <input type="radio" name="sex" value="0">男 
        <input type="radio" name="sex" value="1">女
    
        var sex = document.getElementsByName('sex');
        console.log(sex);




#6.3获取和设置元素中的其他内容

####6.3.1 获取元素名
当我们使用id获取元素的时候，元素的名称回合整个元素一起显示出来，如果想要拿到该元素的元素名，也就是标签名则需要用tagName属性该属性只能获取不能设置。

       var div=document.getElementById("mydiv");
       console.log(div.tagName);//DIV

####6.3.2 获取元素节点里的内容
当获取了元素之后，如果我们要拿到元素中的内容（所有东西），则需要另一种方法得到。元素里的内容可能包括：文本或元素需要用innerHTML

          var div=document.getElementById("mydiv");
          console.log(div.innerHTML);
innerHTML属性除了可以获取标签内的内容外，还可以设置标签的内容。

            var div=document.getElementById("mydiv");
            console.log(div.innerHTML);

            div.innerHTML='您好';

####6.3.3获取元素节点中的文本
利用innerText属性获取的只能是文本节点，不能是其他，当然innerText属性处理获取，也可以设置元素中的文本

            var div=document.getElementById('mydiv')
            console.log(div.innerText);
             
            div.innerHTML='您好';

####6.3.4 获取元素的类名
利用className属性获取元素的类名，义字符串的形式返回。同时可以设置新的class类名，需要注意的是，返回值是一个字符串，如果更换
     
         var div=document.getElementById('mydiv');
         console.log(div.className);



####6.3.5 获取元素样式
style属性可以获取元素内联属性的所有属性，当然如果继续在style中找属性名如：background-color，就可以得到改属性的值，义字符串的形式返回，同时也可以更改该属性，从而达到增加或更改样式，需要注意的是，以js形式增加样式的优先级大于css优先级
            
    <div style="background-color: red;"></div>
    <script>
       var div = document.getElementsByTagName('div');
       //js拿到的是内联
        console.log(div[0].style.backgroundColor);
    </script>

####6.3.6获取元素的属性
getAttribute（''）可以获取元素的某个属性，要将属性名称放在括号中，记得要用引号括起来，返回值就是字符串形式的属性值。
        
         var div = document.getElementById('mydiv');
         var a = document.getElementsByTagName('a');
         console.log(div.getAttribute('date-lj'));
         console.log(a[0].getAttribute('href'));

####6.3.7设置元素属性
setAttribute()可以设置元素的某个属性，第一个参数是属性名，第二个参数是属性值，都需要用引号括起来以逗号分隔。

        var div=document.getElementsByTagName('div');
        var a=document.getElementsByTagName('a');
        //设置元素属性
        div[0].setAttribute('id','mydiv');
        a[0].setAttribute('href','http://www.baidu.com');


####6.3.8 删除元素属性
使用removeAttribute（），可以删除某个元素的某个属性，括号中放入需要删除的属性名，用引号包裹。
removeAttribute（）删除元素

        var div=document.getElementById('mydiv');
        div.removeAttribute('id');



###6.4 增加元素
####6.4.1创建元素节点
利用js创建一个元素的方法是：先在文档中创建一个标签document.createElement（）口号中写标签名，要用字符串形式，创建后不是就存在了，而是需要把这个已经创建的元素放到你想放在的元素（父级元素）中去。
createElement（）创建元素

        //用一个变量承接在文档中创建的一个元素
        var div =document.createElement('div');
        //将已经创建的元素放在想放在的位置
        document.body.appendChild(div);


####6.4.2创建文本节点
利用js创建元素的文本节点，先在文档中创建文本document.createTextNode（‘一段文字’）在括号中将要创建的字符串放入，最后插入到需要的元素中。
document.createTextNode('一段文字');
 
        var p=document.getElementById('p')
        var text=document.createTextNode('一段文字');
        p.appendChild(text);

####6.4.3 css样式赋予
style.cssText是一个css样式集合，他可以把css层叠样式表中的css样式直接放在该属性后，就不需要一条一条去赋予样式，可以一次性赋予样式。
.style.cssText（）赋予样式

       div.style.cssText = 'width:100px;height:100px;background-color:red;'


####6.4.46.4.4  在后元素前插入创建的新元素
insertBefore（）这个函数和appChild（）用法基本一致，都是向父级中插入一个子元素，但区别是insertBefore（）是可以选择插入的位置，它需要插入到某一个元素之前的位置，因此需要哪个子元素，insertBefore（）有两个参数，第一个参数是需要插入的元素，第二个是在谁之前插入，两个参数用逗号隔开。
insertBefore（）在后元素前插入创建的新元素

        <ul id="ul">
			<li id="pg">苹果<>
			<li id="jz">橘子<>
			<li><>
		</ul>
		<script type="text/javascript">
			var ul = document.getElementById('ul');
			var pg = document.getElementById('pg');
			var jz= document.getElementById('jz');
			var li = document.createElement('li');
			//在父级中插入一个元素（插入元素，在谁前面）
			ul.insertBefore(li,jz);
			var t = document.createTextNode('火龙果');
			li.appendChild(t);
		</script>

###6.5删除和替换元素
####6.5.1元素的替换
replaceChild（）
元素的替换，是在父元素中一个子元素需要被另一个新的子元素所替换，使用replaceChild（）方法，该方法有两个参数，第一个是将要替换的新元素，第二个是被替换的旧元素，中间用逗号分割

         var mydiv=document.getElementById('mydiv');
         var myp=document.createElement('p')
         //在父元素中替换子元素，第一个是新的元素，第二个是旧的
         document.body.replaceChild(myp,mydiv)

####6.5.2 元素的删除
removeChild（）
元素的删除是在父元素的其中一个子元素需要删除，使用removeChild（）把需要删除的元素放入括号里

        var mydiv=document.getElementById('mydiv');
        document.body.removeChild(mydiv);

###6.6 查找节点（node）
节点是在dom树上的节点，其中包括元素，文本，属性，注释等等，常用的有三个元素，文本，属性。

####6.6.1 节点属性

        var mydiv = document.getElementById('mydiv');
        console.log(mydiv.nodeName);
        console.log(mydiv.nodeValue);
        console.log(mydiv.nodeType);


####6.6.2 层次节点
节点可以分为：父节点与子节点，兄弟节点，当我们知道其中之一的时候，可以用一些方法找到另一个

####6.6.3 获取所有节点
使用childNodes属性拿到的是该元素下的所有节点，包含所有节点类型，不单单只是元素

        <ul id="myul">
           <li>111</li>
           <li>222</li>
           <li>333</li>
        </ul>
       <script>
           var myul=document.getElementById('myul');
           //这个方法是所有节点
           console.log(myul.childNodes)
       </script>

####6.6.4 获取第一个和最后一个子节点
   用firstChild和lastChild可以拿到该父元素下的第一个和最后一个子节点，注意不一定是元素节点

    <ul id="myul"><li>111</li><li>222</li><li>333</li></ul>
    <script>
         var myul=document.getElementById('myul');
         console.log(myul.firstChild);
         console.log(myul.lastChild);
    </script>


####6.6.5 获取父节点
使用.parentNode属性可以拿到该元素的父节点，注意父节点只有一个

    <ul id="myul"><li>111</li><li>222</li><li>333</li></ul>
    <script>
        var myul=document.getElementById('myul');
        console.log(myul.parentNode);
    </script>

####6.6.6 获取兄弟节点
使用previousSibling，nextSibling可以获取该元素的前一个或后一个兄弟节点，只能获取一个

    <h2></h2><div id="mydiv"></div><p></p>
    <script>
        var mydiv=document.getElementById('mydiv');
        console.log(mydiv.previousSibling);
        console.log(mydiv.nextSibling);
    </script>


###6.7 元素的宽高属性
####6.7.1 offsetWidth和offsetHeight属性
需要获取一个元素的宽度个高度，使用style是无法获取的，所以我们选择使用offsetWidth和offsetHeight属性，该属性可以获取元素的站位宽高，也包含了内边距和边框


     <div id="mydiv"></div>
    <script>
       var mydiv=document.getElementById('mydiv');
       console.log(mydiv.style)//这种方法只能拿到内联
       console.log(mydiv.offsetWidth);

    </script>

####6.7.2 clientWidth和clientHeight属性

clientWidth和clientHeight属性也可以获取元素的宽高，但是与offsetWidth和offsetHeight属性不同的是不包含边框

       console.log(mydiv.clientWidth);


###6.8 子元素与父元素的距离
offsetLeft和offsetTop是距离body左边界和上边界的距离，但该子元素使用了定位属性，则offsetLeft和offsetTop参照的就不再是body而是距离他最近的父元素


       <div id="baba"><div id="erzi"></div></div>
    
       <script>
          var rezi=document.getElementById('erzi');
          console.log(erzi.offsetLeft);
          console.log(erzi.offsetTop);
       </script>



##练习：
  随便一个标签给他一个id
  获取这个元素的标签名
  如果元素是加粗的就变成不加粗

        <h1 id="p">今天周一，一天满课</h1>
        <script>
        var p=document.getElementById("p");
        console.log(p.tagName);
        //方法1
        // if(p.tagName=="H1"||p.tagName=="H2"||p.tagName=="H3"||p.tagName=="H4"||p.tagName=="H5"||p.tagName=="H6"||p.tagName=="B"||p.tagName=="STRONG"){
        //     p.style.fontWeight=400;
        // }

        //方法2
        //哪些是加粗标签h1 h2 h3 h4 h5 h6 b strong
        //不管是不是粗体，统一变为细体
        //  p.style.fontWeight=400;

         //方法三
         var arr=['H1','H2','H3','H4','H5','H6','B','STRONG'];
         var isTure=arr.indexOf(p.tagName);
         console.log(isTure);
         if(isTure != -1){
            p.style.fontWeight=400;
            p.style.color='red';
         }
    </script>


需求2
 1.在一个列表标签中，插入三个无序内容块
 2.内容为：苹果 西瓜 草莓


需求3
1 HTML里任何标签都不要写
2 js在body创建ul 包括三个li
3 第二个li背景颜色蓝色

       <style>
       .blue{
           background-color: blue;
       }
    </style>
     </head>
     <body>
    <script>
        document.body.innerHTML = '<ul><li>1</li><li>2</li><li>3</li></ul>';
        document.getElementsByTagName('li')[1].setAttribute('class','blue');      
    </script>