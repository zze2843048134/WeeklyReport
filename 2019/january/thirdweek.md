##  2019-01-19 第三周总结
**项目名：《我是球星》**  
**负责人：钟子恩**

> ### 本周工作内容
> 
> * 星期一:
> > 1.研究 Activity 切换动画
> >> * 期望效果：搞清楚 Activity 转场动画的设置和使用
> >> * 完成情况：完成，继续推进
> >> * 研究成果：设置方式有两种，首先他们都需要在 res->anim 文件夹创建动画的 xml 文件。然后第一种：在 style.xml 文件定义 activity...Animation 或者 window...Animation 属性，然后在 manifest.xm 文件中给 Activity 设置主题。或给 application 设置全局主题；第二种：在代码中 startActivity 或 finish 后调用 overridePendingTransition 方法，其中参数 enterAnim 代表进入屏幕的 Activity 执行的动画，参数 exitAnim 代表退出屏幕的 Activity 执行的动画。个人偏好第二种方法。
> 
> * 星期二： 
> > 1.研究 Fragment 转场动画
> >> * 期望效果：搞清楚 Fragment 转场动画的设置和使用
> >> * 完成情况：完成，继续推进
> >> * 研究成果：设置方式和 Activity 类似，都需要在 res->anim 文件夹创建动画的 xml 文件。 Fragment 是在 FragmentTransaction 调用 commit 之前调用 setCustomAnimations 设置动画，并且要把 Fragment 加入回退栈中，即调用 addToBackStack 方法。
> >> * 疑难问题：对 Fragment 的转场动画设置视差效果发现进入屏幕的 Fragment 在退出主屏幕的 Fragment 之下；对源码进行了研究初步发现这个原因是 Fragment 栈操作导致，也就是源码问题。可以通过 SwipeBackLayout 插件解决。
> 
> * 星期三:
> > 1.研究 share 转场动画
> >> * 期望效果：可以使用 share 动画实现微信朋友圈查看大图转场效果。
> >> * 完成情况：完成
> >> * 研究成果：可参照[传送门](https://blog.csdn.net/qq_21138819/article/details/85293801),其中需要说明的是在 ActivityCompat.setExitSharedElementCallback(Activity, SharedElementCallback) 的参数 SharedElementCallback 的 onMapSharedElements 方法最后需要调用 setExitSharedElementCallback 否则再次转场会出现错位。
> 
> * 星期四:
> > 1.修复大数据 UI 兼容问题
> >> * 期望效果：可以兼容各种屏幕
> >> * 完成情况：已完成
> >> * 问题原因：素材图片不能满足多种屏幕。
> >> * 解法方法：加载素材图片，并对图片进行计算缩放。
> 
> > 2.修复赛事主页猜球不能猜球
> >> * 期望效果：可以猜球
> >> * 完成情况：已完成
> >> * 问题原因：猜球状态在逻辑上的错误。
> >> * 解决方法：对逻辑调整。
> 
> * 星期五:
> > 1.新增用户协议
> >> * 期望效果：展示用户须知协议
> >> * 完成情况：已完成
> >> * 疑难问题：设置 ClickableSpan 的 view 同时需要设置 setMovementMethod 方法否则文字区域点击没有反应；另外 setHighlightColor 是可选设置，用于设置 文字区域的背景颜色。
> 
> > 2.发布 5.3.0 版本
> >> * 完成情况：已完成

-------------------------------------------------------------------

> ### 工作的收获
> 
> 1. 巩固了对 Activity 和 Fragment 转场动画使用的认识。
> 2. 对转场动画有了更对的了解，并学会类 share 动画的使用。
> 3. 对 Fragment 的执行过程在源码上的执行有了基础的认识。
> 4. 学习了 Spannable 家族中可点击的 Spannable 的使用，并有了实践经验。

-------------------------------------------------------------------

> ### 工作中的不足
> 
> 1. 对动画的了解只在基础不够深入，包括动画的类型，使用方式，实现过程。
> 2. 对 Fragment 虽然有比较多的认识，但是在源码上的了解知之甚少。
> 3. TextView 的绘制和点击等实现过程不够深入透彻。

-------------------------------------------------------------------

> ### 上周工作计划
> 
> 1. 转场动画的研究和迭代  
>    进度：继续推进
> 2. 通过图片缩放平移研究触摸手势组件  
>    进度：继续推进

-------------------------------------------------------------------

> ### 下周工作计划
> 
> 1. TextView 源码研究。
> 2. 推进通过图片缩放平移研究触摸手势组件。