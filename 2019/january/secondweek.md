##	2019-01-12 第二周总结
**项目名：《我是球星》**  
**负责人：钟子恩**

> ### 本周工作内容
>
> * 星期一:
> > 1.实现沉浸式主题使用工具类。
> >> * 期望效果：可以适配各种实现方式的标题
> >> * 完成情况：已完成
> 
> > 2.toolbar基本使用和自定义。
> >> * 期望效果：可以正确适配沉浸式主题效果。
> >> * 完成情况：已完成
> >> * 问题原因：自定义toolbar，发现gravity = bottom 时候，内嵌布局底部溢出toolbar布局，以及布局左边留有marginStart。具体原因可以在源码中：onLayout -> layoutChildLeft -> getChildTop 中找到答案。
> >> * 解决方法：给toolbar设置 contentInsetStart = 0 可以取消左边marginStart；设置 minHeight = 0 可解决内嵌布局底部溢出问题。
>
> * 星期二:
> > 1.对项目进行沉浸式主题。
> >> * 期望效果：可以正确展示沉浸式主题。
> >> * 完成情况：待完成
>
> * 星期三:
> > 1.进一步完成项目沉浸式主题迭代，并修复迭代后出的一些问题。
> >> * 期望效果：同星期二
> >> * 完成情况：已完成
> 
> * 星期四:
> > 1.赛程类列表优化。
> >> * 期望效果：列表滑动流畅。
> >> * 完成情况: 已完成
> >> * 问题原因：布局层次过多造成过度绘制现象。
> >> * 解决方法：减少布局层次，并使用自定义 span 取代向layout中添加TextView展示标题的方式。
> >> * 疑难问题：当标签内容不包含双字节字符时候无法正确展示标签，具体原因不详；但可以在字符串末尾加 \\b，然后设置 setSpan 的 end < 字符串长度既可。也可以通过 setText 的 type = BufferType.SPANNABLE，但会使得其它 type 类型的 span 无法显示，具体原因不详。
>
> * 星期五:
> > 1.适配消息提示权限。
> >> * 期望效果：如果APP没有消息权限，那么第一次打开APP时候向用户申请权限。
> >> * 完成情况：已完成

-------------------------------------------------------------------

> ### 工作的收获
> 
> 1. 自定义 toolbar 设置 gravity = bottom 内嵌布局底部会溢出 toolbar，可以通过设置 minHight = 0 来解决这个问题，原因可从源码 onLayout -> layoutChildLeft -> getChildTop 执行链中找到。而内嵌布局左边默认的 marginStart 可以同过设置 contentInsetStart = 0 解决，原因可在 onLayout 总找到；右边默认 marginEnd 解决方法同理。
> 2. 沉浸式主题，4.4以上才有这个设置，而4.4只可以通过设置状态栏半透明的方式设置沉浸式主题。5.0以上可以通过设置状态栏颜色来适配沉浸式主题，其中浅色主题会导致状态栏内容显示不清晰，6.0以上(包括6.0)可以通过设置SYSTEM_UI_FLAG_LIGHT_STATUS_BAR 属性解决状态栏内容显示不清晰，5.0~6.0(不包括6.0)可以通过给状态栏设置alpha值来解决以上问题。请参考**[传送门](https://www.jianshu.com/p/dc20e98b9a90)**
> 3. 自定义 span 需要继承 ReplacementSpan 来实现，请参考**[传送门](https://blog.csdn.net/industriously/article/details/53493392?utm_source=blogxgwz7)**。值得注意的是如果自定义 span 包含的内容是非双字节字符，并且 setSpan 的 end - start = string.length 那么内容将不会显示在界面上，解决方案有两种；第一种解决方案是在字符串末尾加 \\b，并且设置 end - start < string.length；第二种解决方案是 setText 的 type = BufferType.SPANNABLE ，但会使得其它 type 类型的 span 无法显示，具体有待研究。
> 4. 消息权限机制，使用 AppOpsManager 通过反射调用 checkOpNoThrow 函数检查是否有消息权限。然后去开启消息权限。值得注意的是 5.0(包括5.0)以上设置 action = "android.settings.APP_NOTIFICATION_SETTINGS" 传递参数 "app_package"，"app_uid",4.4~5.0(不包括5.0)设置 action = Settings.ACTION_APPLICATION_DETAILS_SETTINGS ，category = Intent.CATEGORY_DEFAULT，data = Uri.parse("package:设置项目的包名")。[传送门](https://blog.csdn.net/wuhongqi0012/article/details/68946738)

-------------------------------------------------------------------

> ### 工作中的不足
> 
> 1. 对 TextView 源码的机制了解不足
> 2. 对 权限机制的工作流程知之甚少

-------------------------------------------------------------------

> ### 上周工作计划
> 
> 1. 页面迭代成沉浸式  
>    进度：完成
> 
> 2. 列表滑动流畅度优化  
>    进度：完成
>    
> 3. 通知权限优化  
>    进度：完成
>    
> 4. 通过图片缩放平移研究触摸手势组件  
>    进度：未完成  
>    原因：研究方面的优先级较低，故未完成。

-------------------------------------------------------------------

> ### 下周工作计划
> 
> 1. 转场动画的研究和迭代
> 2. 通过图片缩放平移研究触摸手势组件
