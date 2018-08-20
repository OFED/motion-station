# 动效驿站

>目录

```bash
# canvas相关内容的文章或教程链接：

# svg相关内容的文章或教程链接：

# css3相关内容的文章或教程链接：

```
![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/canvas01.gif)

首先给大家普及一下到底什么是动效。**动效**顾名思义，就是动画效果。

那同学可能不禁想问，那动效这货到底有什么用？有句话说得好：“好看的皮囊千篇一律，有趣的灵魂万里挑一”，所以我们的动效就是干这事儿的，可以让我们的产品或者说前端的页面效果看上去更有趣，更吸引人。

**动效驿站**，这里涵盖了各种实现动效的方法，力在打造动效聚集地，让所有喜欢动效的朋友们都能够汇聚于此，大家共同讨论，共同成长。

这里说到动效的各种实现方法，那势必要先简单说一下动效到底都涵盖哪些技术，以及其所适用的场景：
## GIF
谈到GIF是我们做前端再熟悉不过的了。一方面它制作简单，质量小可压缩，并且制作成本低，很多软件都可以胜任，如PhotoShop,Flash,AE等，都可以导出Gif格式，供前端开发同学使用，另一方，它兼容性强，基本所有浏览器都支持，算是轻量级的动画格式；

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/04.gif)

[原图链接](http://img.ui.cn/data/file/0/4/5/1923540.gif)

当然了，凡事都有两面性，Gif格式的图片缺点也很明显，色彩有限制，单帧只能有256色，无法与用户交互，只能单纯展示，并且帧数不能过多，否则文件可能过大，导致页面卡顿，而且色彩也会损失。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/03.gif)

[原图链接](http://img.ui.cn/data/file/8/2/5/1923528.gif)

优点和缺点我们都已经了解了，那么我们再来说说它的适用场景,我们接触最多的就是loading，以及一些小标签等，所以Gif动画一般适用于页面的细节部分。

当然也会有很多复杂的，比如说法国的动效大神Guillaume Kurkdjian 的作品：
感兴趣的可以戳大神官网：[Guillaume Kurkdjian](https://guillaumekurkdjian.com/) （可能需要科学上网，才能大饱眼福）

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/05.gif)

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/07.gif)

## 逐帧动画
我们刚刚在谈到Gif的时候有说到帧的概念，帧我们可以理解为是静态的图片，比如在视频剪辑的时候每秒24帧，就是每秒钟闪过24张静态图片的意思；所以在固定的时间里播放固定帧数的图片就是我们认识的Gif。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/zhuzhen01.jpg)

而逐帧动画呢和Gif甚有渊源，就是动画的静态图片放在那里，标好第一张，第二张，。。。最后一张，让后通过CSS,JS来控制它的步骤，如css3中的step(),和animation中的background-position,来控制动画实现的一种手段；

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/zhuzhen02.gif)

[实例图片链接](http://www.ui.cn/detail/93427.html)

举个例子，这里有两张图是小编从UI中国上搜罗到的，我们经常会遇到这样的一种场景，我们访问的页面的时候，偶尔会因为种种原因打不开，因此我们会做异常处理，404页面是最常见的一种情况，如果直接上第一张图也算是中规中矩，可是如果能用第二张图gif, 用小船说翻就翻来解释404的含义，是不是既形象又生动。

好，那么问题来了，假如这个gif的质量很大，那么我们无论在移动端还是pc端来加载这样的图片，不仅会过慢，而且还会浪费用户的流量，甚至因为性能问题引起手机耗电多，发烫等等。。。那么逐帧动画就应运而生了，同学可以看下图，是图二的gif在时间轴上的部分截图，逐帧动画简单理解，就是在不影响动画展示的前提下，在时间轴上提取关键帧，然后通过上面讲过的方式来用代码控制图片，来形成动画的一种手段。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/zhuzhen03.png)

所以相比较Gif而言，逐帧动画更灵活，可表现的内容更丰富；

## CSS3动效
css3相信大家一定不陌生，其中的动画(Animation)是css3的亮点之一。可以通过animation属性指定@keyframe来完成关键帧动画。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/css3-01.gif)

此外，其核心是应用Transform, Transition, Animation等各种属性的交叉配合使用，来实现复杂的动画效果。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/css3-02.gif)

css3在性能上会稍微好些，浏览器会对css3动画做一些优化；当然缺点也很明显，一方面动画控制不够灵活，另一方面个别浏览器兼容不够友好；而且，有些动画功能无法实现，依然要借助于原生javascript来实现。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/css3-03.gif)

所以复杂的动画还是用javascript来实现比较靠谱，一些小的交互动效再考虑css3吧；

## SVG
SVG (Scalable Vector Graphics),指的是可伸缩的矢量图形，用来定义用于网络的基于矢量的图形。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/svg01.gif)

它擅长于线条的动画，和其他格式的图像比起来，有很多优点。

例如：非常多的工具可以读取并且编辑它，比如记事本；同JPEG，GIF相比，尺寸更小，且可压缩性更强；可以在像素不下降的情况下被放大；图像文本可选，也可以搜索，适合制作地图等。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/svg02.gif)


当然缺点也很明显，就是DOM会比正常的图形慢一些，而且如果其节点多而杂，就会更慢；不能动态的修改动画的内容；不能与HTML内容集成；而且想制作SVG动画，还需要会使用AI工具的UI同学来帮忙才可以。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/svg04.gif)

svg这部分配图源自于Airbnb团队的Lottie动效库, 而且支持的很全面：Lottie for Android, iOS, React Native, and Web等。感谢这样的团队为社区做出的贡献！
感兴趣的同学可以直接戳这里：[Lottie动效库官网](http://airbnb.io/lottie/)

当然后期我们也会开展一些这方面的使用教程，欢迎大家持续关注动效驿站的动态！(最好先收藏起来，然后点个赞，再分享一下，小编拜谢！哈哈)

## Canvas
canvas是HTML5的一个新的元素，和画板很类似，拥有很多绘制路径，矩形，图形，字符以及添加图像的方法；canvas本身是没有绘图的能力的，所以需要依赖JavaScript来完成。所以可以这么理解，canvas是擅长绘画的动画。

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/canvas02.gif)

有猿友称，canvas是svg的兄弟，大部分的图表动画等，都是由canvas 或者 svg制作成的，当然也会有一些区别：

![Alt img](https://raw.githubusercontent.com/OFED/motion-station/master/static/imgs/canvas03.gif)

canvas是画框，有自己固定的高宽，svg是不依赖分辨率的矢量，可以任意放大缩小；
canvas能以.jpg的格式保存图像，svg是文本的格式保存图像；
canvas绘制的图像不占DOM，而svg的每个图像都是1个DOM元素；
canvas适合图像密集型的动画，而svg不适合大量使用；
canvas完全依赖脚本绘制作，而svg可直接使用矢量转存生成；

以上这些，就是小编总结的一些关于动效的知识，希望大家能够喜欢，如果对你又一些帮助的话，劳烦看一下屏幕的上下左右，点个赞，收个藏，分个享，再次拜谢 !!! 🙏 
