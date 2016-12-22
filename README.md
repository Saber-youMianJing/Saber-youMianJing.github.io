# Parallax.Js
***
>Parallax.js 是一个简单的，轻量级的的视差引擎，能够对智能设备的方向作出反应。在没有没有陀螺仪或运动检测硬件可用的时候，使用光标的位置来代替。有很多的行为，你就可以设置为任何给定的视差实例。这些行为既可以通过在标记中指定的数据属性或通过构造函数 和 JavaScript API 调用。

### 如何使用
~~~html
<script src="../deploy/jquery.parallax.js"></script>
<script type="text/javascript">
var scene = document.getElementById('scene');
var parallax = new Parallax(scene);
//native
  $('#scene').parallax();//jquery
</script> 
~~~
#### 先看一下可以做什么
[Demo][5]
~~~html
<ul id="scene" class="scene">
	<li class="layer" data-depth="0.00"></li>
	<li class="layer" data-depth="0.20">
		<div class="background"></div>
	</li>
	<li class="layer" data-depth="1.40">
		<img src="images/board-cloud-3.png">
	</li>
	<li class="layer" data-depth="2.60">
		<img src="images/board-cloud-4.png">
	</li>
	<li class="layer" data-depth="3.80">
		<img src="images/board-cloud-3.png">
	</li>
	<li class="layer" data-depth="5.00">
		<img src="images/board-cloud-2.png">
	</li>
</ul>
~~~
* HTML结构
>该视觉差特效的基本HTML结构使用的是一个无序列表，每一个列表项给它们一个class layer和一个data-depth属性来指定该层的深度。深度为0的层将是固定不动的，深度为1的层运动效果最激烈的层。0-1之间的层会根据值来相对移动。
### 初始化及参数
| 参数        | 值           | 描述 |
| ------------- |:-------------:| -----:|
| calibrate-x，-y | true 或false | 指定是否根据初始时x或y轴的值来计算运动量 |
| invert-x,-y      | true 或false |   设置为true则按反方向运动层 |
| limit-x,-y | number 或false |   x,y方向上总的运动量数值范围，设置为false则允许层自由运动 |
| scalar-x,-y | number |  输入的运动量和这个值相乘，增加或减少层运动的灵敏度 |
| friction-x,-y | number |  层运动的摩擦量，实际上是在层上添加一些easing效果 |
|origin-x,-y | number |  鼠标输入的x原点，默认值是0.5。0会移动原点到页面的左边，1会移动原点到页面的右边。 |

* 层运动的计算规则
>每一个层的运动量依赖于3个因素：
scalarX和scalarY的值
父DOM元素的尺寸大小
一个parallax场景中层的depth值
计算的公式如下：
xMotion = parentElement.width  * (scalarX / 100) * layerDepth
yMotion = parentElement.height * (scalarY / 100) * layerDepth
***
#### 基本步骤说完了，接下来我们看一下视差网站的效果
参考myindex.html
***

## Skrollr+Parallax
* 两个使用方式和展示效果都不同的视差插件都看完了，都对视差效果有一定的限制所以下面我们来看一下2个插件一起使用可以做出什么样的效果

这个Demo是通过一个视差网站利用S+P仿制的，网站原本没有使用这2个插件，但是用我们的这2个插件也可以做出同样的效果，最后这个网站我们来看一下
http://kennedyandoswald.com/#!/premiere-screen
