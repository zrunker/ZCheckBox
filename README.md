# ZCheckBox
Android中CheckBox自定义样式和扩大点击区域的实现。使用工具Android Studio
>作者：邹峰立，微博：zrunker，邮箱：zrunker@yahoo.com，微信公众号：书客创作，个人平台：[www.ibooker.cc](http://www.ibooker.cc)。

>本文选自[书客创作](http://www.ibooker.cc)平台第18篇文章。[阅读原文](http://www.ibooker.cc/article/18/detail) 。

![书客创作](http://upload-images.jianshu.io/upload_images/3480018-5ccf011feef834fb..jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

​Android中CheckBox的使用频率是相当高的，但是很多时候系统自带的样式和效果并不能满足实际项目需求，所以知道怎么去自定义样式和扩大CheckBox点击区域还是相当重要的。

![四种样式结果图](http://upload-images.jianshu.io/upload_images/3480018-b7f599f35cb659a7..jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

上面的[四种样式结果图]，是**开启手机布局边界**之后的截图，通过截图可以看出第三种结果样式才是我们想要的。

CheckBox继承CompoundButton，而CompoundButton基础Button，按照常理讲，Button所具有的功能CheckBox都会有，但是有一些地方用法却不尽相同。例如Padding属性，CheckBox设置Padding实际上，你会发现它只是设置了到右侧的距离。

**1、系统默认CheckBox。**
```
<!--系统默认效果CheckBox-->
<CheckBox
   android:id="@+id/checkbox1"
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:padding="10dp"/>
```
**2、自定义样式CheckBox。**

这里牵扯到CheckBox的另外一个属性android:button=“”，该属性是用来设置CheckBox的button样式（非专业说法），这里的button样式包括，状态如选中，按下等，样式如背景等。
```
<!--自定义样式CheckBox-->
<CheckBox
   android:id="@+id/checkbox2"
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:button="@drawable/bg_checkbox_one"
   android:padding="10dp"/>
```
这里的样式XML文件，只需要通过<selector>设置CheckBox的四种状态即可。<selector>为布局选择器。
```
<selector xmlns:android="http://schemas.android.com/apk/res/android">
   <item android:drawable="@mipmap/icon_check_selected" android:state_checked="true"/>
   <item android:drawable="@mipmap/icon_check_selected" android:state_selected="true"/>
   <item android:drawable="@mipmap/icon_check_selected" android:state_pressed="true"/>
   <item android:drawable="@mipmap/icon_check_default" android:state_checked="false"/>
</selector>
```
**3、自定义样式+扩大点击区域CheckBox。**

方式二中虽然改变了CheckBox的样式，但是却没法真正的改变CheckBox的点击区域，那么采用哪种方式来处理这一问题尼？既然CheckBox继承了CompoundButton，那么我们可以把CheckBox当成一个Button来进行处理，下面便是通过设置android:drawableLeft解决这一问题。
```
<!--自定义样式+扩大点击区域CheckBox-->
<CheckBox
   android:id="@+id/checkbox3"
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:button="@null"
   android:drawableLeft="@drawable/bg_checkbox_one"
   android:drawableStart="@drawable/bg_checkbox_one"
   android:padding="10dp"/>
```
**4、错误使用方式CheckBox。**

方式三中通过设置CheckBox的android:drawableLeft属性实现自定义样式+扩大点击区域，那么有人会想，如果通过设置android:background属性来实现岂不是更好，但是使用android:background的方式，会是CheckBox样式变形，所以这是一种错误的方式。
```
<!--错误使用方式CheckBox-->
<CheckBox
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:background="@drawable/bg_checkbox_one"
   android:button="@null"
   android:padding="10dp"/>
```
[GitHub地址](https://github.com/zrunker/ZCheckBox)
[阅读原文](http://www.ibooker.cc/article/18/detail) 

----------
![微信公众号：书客创作](http://upload-images.jianshu.io/upload_images/3480018-e2f13f71fa894197..jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
