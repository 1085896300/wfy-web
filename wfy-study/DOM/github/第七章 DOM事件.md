# 第七章 DOM事件
###7.1 鼠标和键盘事件
####7.1.1 鼠标事件

单一作用于某个元素的事件


       //点击事件
        //  mydiv.onclick=function(){
        //      alert('点击事件');
        //  }
         //双击事件
        //  mydiv.ondblclick=function(){
        //      alert('双击事件');
        //  }


         //鼠标按下
        //  mydiv.onmousedown=function(){
        //     mydiv.innerHTML='按下事件';
        //  }
         //鼠标抬起
        //  mydiv.onmouseup=function(){
        //     mydiv.innerHTML='';
        //  }


          //鼠标移动
          //需要注意，只要鼠标移动就触发
        //   document.onmousemove=function(){
        //       console.log('移动了');
        //   }
        //   mydiv.onmousemove=function(){
        //       console.log('div');
        //   }


        //鼠标移入
        //会触发冒泡（从内逐级向外依次触发）
        // mydiv.onmouseover=function(){
        //     console.log('红');
        // }
        // box.onmouseover=function(){
        //     console.log('蓝');
        // }
        //会触发多次，取决于鼠标位置和嵌套
        // mydiv.onmouseout=function(){
        //     console.log('离开红');
        // }
        // box.onmouseout=function(){
        //     console.log('离开蓝');
        // }


        //不会进行多次触发
        mydiv.onmouseenter=function(){
            console.log('红');
        }
        box.onmouseenter=function(){
            console.log('蓝');
        }
        //鼠标移出
        mydiv.onmouseleave=function(){
            console.log('离开红');
        }
        box.onmouseleave=function(){
            console.log('离开蓝');
        }


鼠标移入移除情况：

第一套：会多次触发
       
        //会触发冒泡（从内逐级向外依次触发）
        // mydiv.onmouseover=function(){
        //     console.log('红');
        // }
        // box.onmouseover=function(){
        //     console.log('蓝');
        // }
        //会触发多次，取决于鼠标位置和嵌套
        // mydiv.onmouseout=function(){
        //     console.log('离开红');
        // }
        // box.onmouseout=function(){
        //     console.log('离开蓝');
        // }

第二套：不会多次触发

       //鼠标移入
       //不会进行多次触发
        mydiv.onmouseenter=function(){
            console.log('红');
        }
        box.onmouseenter=function(){
            console.log('蓝');
        }

        //鼠标移出
        mydiv.onmouseleave=function(){
            console.log('离开红');
        }
        box.onmouseleave=function(){
            console.log('离开蓝');
        }

####7.1.2 键盘事件
onkeydown(),onkeyup()
键盘的按钮按下时会触发onkeydown事件，在函数中的e参数代表的是哪一事件触发的。

       document.onkeyup=function(e){
              alert('按下')
        }

      
键盘的抬起会触发onkeyup事件，他的用法与onkeydown一样

      document.onkeyup=function(e){
              alert('抬起')
        }

###7.2 Event事件对象
####7.2.1 Event事件对象的概念
   Event对象代表事件的状态，比如事件在其中发生的元素，键盘按键的状态，鼠标的位置，鼠标按钮的状态

####7.2.1 Event事件对象产生的事件
当用户单击某个元素的时候,我们给这个元素注册的事件就会触发,该事件的本质就是一个函数,而该函数的形参接收一个event对象.
事件通常与函数结合使用，函数不会在事件发生前被执行！


####7.2.3 接收方式
通过事件触发时的函数，以参数的形式传递该函数内。不用靠调用传参，也就是说event对象是事件触发时调用函数的第一个参数
         var mydiv=document.getElementById('mydiv');
          document.onclick=function(){
              akert(1);
          }
####7.2.4 event对象的常用属性
鼠标的坐标轴

             //x轴
             console.log(e.clientX);
             //Y轴
             console.log(e.clientY);

键盘的值

             e.keyCode


####7.2.5 event的兼容性
event对象根据不同的浏览器他的获取是不同的方法，以下是针对获取event对象的兼容性写法.


          //事件触发时    调用的函数（event）
         document.onclick=function(e){
             //   非IE   低版本IE
             var ev=e||window.event;
             //x轴
             console.log(ev.clientX);
             //Y轴
             console.log(e.clientY);
         }


###7.3  对象事件
####7.3.1 页面（元素）加载完成后执行
 window.onload是等待页面加载之后执行函数的内容，但是函数没有重载，也就是说window.onload只能写一次,


           //页面加载完成后执行的代码段
        window.onload=function(){
            var mudiv = document.getElementById('mydiv');
            mydiv.onclick=function(){
              alert(mydiv.tagName);
            }
        }     



###7.4 表单事件