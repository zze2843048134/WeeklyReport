## 2019-02-23 第一周周报  

**项目名：《我是球星》**  
**负责人：钟子恩**

> ### 本周工作内容
> 
> * 星期一：
> > 1.修复进入直播间 crash
> >> * 期望效果：进入直播不会 crash
> >> * 完成情况：已完成
> >> * 问题原因：OnDrawListener 完成后，在 onDraw() 方法中 removeOnDrawListener 会导致 crash。具体原因参考源码。
> >> * 解决方法：使用 OnPreDrawListener 取代 OnDrawListener 即可。
> 
> > 2.组委会直播不受直播次数影响
> >> * 完成情况：已完成。
>
> > 3.修复直播间分享 crash
> >> * 期望结果：直播间分享不会 crash。
> >> * 完成情况：已完成。
> >> * 问题原因：直播间是横屏，分享界面是直屏。从横屏跳转到直屏会触发原来横屏的界面切换成直屏，这个过程会触发 Android 的生命周期，先把原来的屏幕销毁在重建的过程。这个过程导致原来界面信息丢失。
> >> * 解决方法：在 manifest.xml 相应的 activity 标签加上 android:configChanges="keyboardHidden|orientation|screenSize" 即可确保屏幕不被销毁。
> 
> * 星期二：
> > 1.学习 groovy 语法，学习 gradle 使用方式
> >> * 完成情况：继续推进。
> 
> * 星期三：
> > 1.学习 gradle 使用方式
> >> * 完成情况：继续推荐。
> 
> * 星期四：
> > 1.修复我的生涯 crash
> >> * 期望结果：不发生 crash。
> >> * 完成情况：已完成。
> >> * 问题原因：标记页面的 TAG 获取了 AbstractActivity 的静态名称。
> >> * 解决方法：获取当前对象的类名称。
> 
> > 2.修复赛事报名分享，展示文案不一致
> >> * 完成情况：已完成。
> 
> > 3.全局管理项目依赖的版本号。
> >> * 完成情况：已完成。
> 
> * 星期五：
> > 1.修复直播信息时间显示不对
> >> * 完成情况：已完成。
> 
> > 2.修复直播广告造成界面无法操作的问题。
> >> * 期望结果：直播间功能可以，正常操作。
> >> * 完成情况：已完成。
> >> * 问题原因：广播一直占用主线程。
> >> * 解决方法：设置一个时间间隔。

-------------------------------------------------------------------

> ### 工作的收获
> 
> 1.回顾了 activity 生命周期
> 2.学习了 groovy 的基本语法。

-------------------------------------------------------------------

> ### 工作的不足
> 
> 1.groovy 的语法和对 gradle 使用生疏。
> 2.对一些基础知识有所遗忘。