
# html、css 学习 （不定期更新）

*弹性盒子-子级宽度分配不均*

        解决：子级设置 ： width：0;
        
*transition 多个属性值*

        1、ease：（逐渐变慢）默认值，ease函数等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0).
        
        2、linear：（匀速），linear 函数等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0).
        
        3、ease-in：(加速)，ease-in 函数等同于贝塞尔曲线(0.42, 0, 1.0, 1.0).
        
        4、ease-out：（减速），ease-out 函数等同于贝塞尔曲线(0, 0, 0.58, 1.0).
        
        5、ease-in-out：（加速然后减速），ease-in-out 函数等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)
        
        6、cubic-bezier：（该值允许你去自定义一个时间曲线）， 特定的cubic-bezier曲线。 (x1, y1, x2, y2)四个值特定于曲线上点P1和点P2。所有值需在[0, 1]区域内，否则无效。

*鼠标连续点击a标签，全部选中变蓝色*

         .ie7 {
             display: inline-block;
             *zoom: 1;
             *display: inline;
         }
         
*ie7下display: inline-block失效*

        .box{
             display: inline-block;
             *zoom: 1;
             *display: inline;
         }
         
*ie6、ie7、ie8中overflow:hidden无效*

        ----产生原因：
        
        当父元素的直接子元素或者下级子元素的样式拥有position:relative属性时，父元素的overflow:hidden属性就会失效。
        ----解决办法：
        我们在IE 6内发现子元素会超出父元素设定的高度，即使父元素设置了overflow:hidden。
        解决这个bug很简单，在父元素中使用position:relative;即可解决该bug
        
        ie7和ie6
        发现在ie6和ie7里面overflow:hidden无效,还是会超出外层div
        后来在外层div上面加上position:relative就解决了
        
*网站排版，读取图片失败，清缓存正常*

        解决：以图片为例， xx.png -->xx.png?v=2这个时候，程序不会在缓存里面找，回到服务器请求。
        
*移动端-点击输入框的瞬间会出现灰色背景*   
     
        input{
            -webkit-text-size-adjust: none;
            -webkit-tap-highlight-color: rgba(0,0,0,0);  
        }
        
*移动端-长按禁止复制选中*      
    
        -moz-user-select: none;
        -webkit-user-select: none;
        
*清除页面滚动条 （此时还是可以滚动，只是看不见滚动条）*   
        
        ::-webkit-scrollbar{
            display: none;
        }
  
*清除浮动*
        
        /*IE下清除浮动*/
        .clearfloat {
            zoom:1;
        }
        /*其他浏览器清除浮动*/
        .clearfloat:after {
            display: block;
            clear: both;
            content: "";
            visibility: hidden;
            height: 0;
        }
        
*清除浮动的几种方式*  
      
      1，父级div定义 height
       
      原理：父级div手动定义height，就解决了父级div无法自动获取到高度的问题。
       
      优点：简单、代码少、容易掌握
       
      缺点：只适合高度固定的布局，要给出精确的高度，如果高度和父级div不一样时，会产生问题
       
      建议：不推荐使用，只建议高度固定的布局时使用
       
      2，结尾处加空div标签 clear:both
       
      原理：添加一个空div，利用css提高的clear:both清除浮动，让父级div能自动获取到高度
       
      优点：简单、代码少、浏览器支持好、不容易出现怪问题
       
      缺点：不少初学者不理解原理；如果页面浮动布局多，就要增加很多空div，让人感觉很不好
       
      建议：不推荐使用，但此方法是以前主要使用的一种清除浮动方法
       
      3，父级div定义 伪类:after 和 zoom
       
      原理：IE8以上和非IE浏览器才支持:after，原理和方法2有点类似，zoom(IE转有属性)可解决ie6,ie7浮动问题
       
      优点：浏览器支持好、不容易出现怪问题（目前：大型网站都有使用，如：腾迅，网易，新浪等等）
       
      缺点：代码多、不少初学者不理解原理，要两句代码结合使用才能让主流浏览器都支持。
       
      建议：推荐使用，建议定义公共类，以减少CSS代码。
       
      4，父级div定义 overflow:hidden
       
      原理：必须定义width或zoom:1，同时不能定义height，使用overflow:hidden时，浏览器会自动检查浮动区域的高度
       
      优点：简单、代码少、浏览器支持好
       
      缺点：不能和position配合使用，因为超出的尺寸的会被隐藏。
       
      建议：只推荐没有使用position或对overflow:hidden理解比较深的朋友使用。
       
      5，父级div定义 overflow:auto
       
      原理：必须定义width或zoom:1，同时不能定义height，使用overflow:auto时，浏览器会自动检查浮动区域的高度
       
      优点：简单、代码少、浏览器支持好
       
      缺点：内部宽高超过父级div时，会出现滚动条。
       
      建议：不推荐使用，如果你需要出现滚动条或者确保你的代码不会出现滚动条就使用吧。
       
      6，父级div 也一起浮动
       
      原理：所有代码一起浮动，就变成了一个整体
       
      优点：没有优点
       
      缺点：会产生新的浮动问题。
       
      建议：不推荐使用，只作了解。
       
      7，父级div定义 display:table
       
      原理：将div属性变成表格
       
      优点：没有优点
       
      缺点：会产生新的未知问题。
       
      建议：不推荐使用，只作了解。
       
      8，结尾处加 br标签 clear:both
       
      原理：父级div定义zoom:1来解决IE浮动问题，结尾处加 br标签 clear:both
       
      建议：不推荐使用，只作了解。
    
*移动端-flex布局*

        ---第一种
        .flexouter{
            display: box;
            display: -moz-box;
            display: -webkit-box;
            box-orient: vertical;
            -moz-box-orient: vertical;
            -webkit-box-orient: vertical;/*horizontal表横向，vertical表垂直*/
        }
        .index{
            box-flex: 1;
            -moz-box-flex: 1;
            -webkit-box-flex: 1;
        }
        ----第二种
        
        /*父级*/
            display: -webkit-flex;
            display: -moz-flex;
            display: -ms-flex;
            display: flex;
        /*子级*/
         -webkit-flex: 1;
        -moz-flex: 1;
        -ms-flex: 1;
        flex: 1;
        
*时间戳转化为固定格式*

        var newDate=new Date();
        //这里的时间返回格式的函数是固定的写法，需要写成全局
        Date.prototype.format = function(format) {
            var date = {
                "M+": this.getMonth() + 1,
                "d+": this.getDate(),
                "h+": this.getHours(),
                "m+": this.getMinutes(),
                "s+": this.getSeconds(),
                "q+": Math.floor((this.getMonth() + 3) / 3),
                "S+": this.getMilliseconds()
            };
            if (/(y+)/i.test(format)) {
                format = format.replace(RegExp.$1, (this.getFullYear() + '').substr(4 - RegExp.$1.length));
            }
            for (var k in date) {
                if (new RegExp("(" + k + ")").test(format)) {
                    format = format.replace(RegExp.$1, RegExp.$1.length == 1
                        ? date[k] : ("00" + date[k]).substr(("" + date[k]).length));
                }
            }
            return format;
        };
        
        //调用
        newDate.format('yyyy-MM-dd h:m:s')
        
*数据化图表运用*
        
[echarts](http://echarts.baidu.com/examples.html)
         
*css鼠标选中文字改变背景色*

        ::-moz-selection{background:#FFFFFF; color:#000000;} 
        ::selection {background:#FFFFFF; color:#000000; } 
        
*设置font-size:100%的目的和作用*
        
        假如你设置body{font-size:12px;}
        
        　　但h1是不会继承这个12px，它会按照一定百分比增加字号，但如果给h1显试指定font-
        
        　　size:100%;它就会继承body设定的字体大小。
        
        　　1. 它改变了默认的大小。
        
        　　2. 这些元素本身不会继承父体的字体大小，设置了font-size:100%后就能自动继承。
        
*使文字垂直居中==>伪元素*

        //同时也适用于父级高度是百分比的情况
        //父级
        .father{
            xxxxx:xxxxx;
            xxxxx:xxxxx;
        }
        .father:after{
            content:'';
            display:inline-block;
            width:0;
            hight:100%;
            vertical-align:middle;
        }
        //子级
        
        .son{
            xxxxxx:xxxxx;
             display:inline-block;
            vertical-align:middle;
        }
        
## 浏览器兼容性问题及解决方案

[浏览器兼容性](https://juejin.im/post/59a3f2fe6fb9a0249471cbb4)
        