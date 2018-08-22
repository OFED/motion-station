![image](https://raw.githubusercontent.com/OFED/motion-station/master/motion/SVG/svg-progress-bar/imgs/01.png)

在我们工作中，进度条是很常见的，我们常用的进度条绝大部分都是血条似的，就是从左边走到右边，同时并伴随着百分比数值的同步更新；但是在一些特定的场景当中我们也需要圆形的进度条，如同上图所示。

简单描述一下场景，比如我们在玩游戏的时候，会伴随着各种任务，有的任务需要杀一个怪就完成了，可有的需要杀2个，3个，4个。。。这时候我们就需要统计了，看不同任务的完成情况，还是拿上图来说，灰色条代表任务总数，蓝色条代表已经完成的任务数量：

![image](https://raw.githubusercontent.com/OFED/motion-station/master/motion/SVG/svg-progress-bar/imgs/02.png)

比如这就代表了此任务完成了3/4,接下来我们就研究一下如何用svg来实现这样的效果；

那在做这个圆形之前，我们先来分析一下它的实现方式，拿直线来举例子，如果我们能实现这样的效果，那是不是意味着，把直线换成圆周，就可以了呢？

![image](https://raw.githubusercontent.com/OFED/motion-station/master/motion/SVG/svg-progress-bar/imgs/03.png)

对，就是这样的思路。

svg提供了一个范围广泛的stroke属性：

属性名称 | 属性描述
---|---
stroke | 属性定义一条线，文本或元素轮廓颜色；
stroke-width | 属性定义了一条线，文本或元素轮廓厚度；
stroke-dasharray | 属性用于创建虚线；

所以，用stroke-dasharray来设置虚线是我们要谈论的重点。用这个属性用空格分隔的数字来表示“实线 空(间隙)”，如stroke-whith="6 6"。如果数字是奇数个的话，则自动补充为偶数，如stroke-whith="6 4 3", 实际上会自动补充为stroke-whith="6 4 3 6 4 3"。

所以，我们在做这个需求的时候，要保证数字的个数为偶数，换句话说就是“实线虚线为一对CP，不要将其拆开”，这一点至关重要。

比如：

![image](https://raw.githubusercontent.com/OFED/motion-station/master/motion/SVG/svg-progress-bar/imgs/04.png)

```bash
# stroke-dasharray="5 5"

# stroke-dasharray="10 10"

# stroke-dasharray="20 10 5 5 5 10"
```

弄清楚这点后，我们就可以来实线我们的圆环进度条了，这里要注意我们的圆环是两层的，一层当做背景，也就是我们的任务总数，为了好理解我们以下称之为总步数(steps)；上面带颜色部分为我们已经完成的任务步数(finished)。

连接中是已经为大家编写好的代码，用vue实现的：

https://codepen.io/abswill/pen/LJNWVa

相关参数说明，可以参照下表：

参数名称 | 参数说明
---|---
steps | 进度总步数
finished | 进度已经完成步数
dashed | 控制虚线还是实线
dashedWidth | 虚线（间隙）宽度
r | 圆环半径
strokeWidth | 线的厚度
bgStroke | 底部背景颜色
activeStroke | 上方激活颜色

![image](https://raw.githubusercontent.com/OFED/motion-station/master/motion/SVG/svg-progress-bar/imgs/05.png)

相关方法说明，可以参照下表：
方法名称 | 方法说明
---|---
cx() | 圆环半径+边线厚度
width() | 圆环所占区域的宽度
circumference() | 圆周
oneStepWith() | 每部分的弧长（包含虚线）
strokeDasharray1() | 返回底层圆环stroke-dasharray属性值
strokeDasharray2() | 返回上层圆环stroke-dasharray属性值

这里有一个点需要大家注意一下：

```javascript

const result = [];

const width = this.oneStepWith - this.dashedWidth;

for (let i = 1; i <= finished; i += 1) {
if (i !== finished) result.push(width, dashedWidth);
else result.push(width, this.circumference - (width * finished) - (dashedWidth * (finished - 1)));
}

return result.join(' ');

```

上面我们有提到过，就是说stroke-dasharray的属性值要“实虚”结合，成对儿出现，那对于finished已完成的步数而言，传进来已完成的最后一步的虚线长度，应该是圆周中的剩余弧长,  如下图：

![image](https://raw.githubusercontent.com/OFED/motion-station/master/motion/SVG/svg-progress-bar/imgs/06.png)

其次，我们需要把svg旋转90度，因为默认是从0度开始的；还有就是参数dashed，默认值是false虚线，如果需求是实线的圆环，改变成true即可；

好了，以上就是这期svg圆环进度条的分享内容，希望能够对你有所帮助，我们下期见！