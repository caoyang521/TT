# TT
##BaseAdapter使用步骤
  1,创建一个类继承BaseAdapter
  2,创建构造方法
  3,修改getCount()方法返回值为list.size()
  4,修改getItem()方法返回值为list.get(position);
  5,修改getItemId返回值为position
  6,重写getView()方法，设置item内容
##书
<第一行代码>
<Android群英传>
<Android开发艺术探索>

##微信摘录：
  我们到了这里的，不是为了浪费生命。不闲聊，不发无意义的图；不抱怨，不泛泛而谈；
  不低俗，也不愤世嫉俗。技术问题请首先努力独立解决，努力做到言之有物。不发广告。
  如果一定要发红包，请发100以上的。愿大家有所收货。

###Android中View的触摸事件涉及到哪些方法？他们之间有什么关系？
在Android中的View触摸事件处理主要涉及以下三个方法

dispatchTouchEvent()
onInterceptTouchEvent()
onTouchEvent()
View的触摸事件传递，从前到后按照以下顺序

Activity
PhoneWindow
DecorView
子View
他们之间的关系如下

当触摸事件来临时，dispatchTouchEvent()会被调用，它的返回值由onInterceptTouchEvent()和child.dispatchTouchEvent()共同决定
在dispatchTouchEvent()中，onInterceptTouchEvent()会被调用，onInterceptTouchEvent()决定的是当前ViewGroup是否对触摸事件进行拦截，如果返回true，则触摸事件由当前ViewGroup的onTouchEvent()处理，否则触摸事件会被分发到子View，由子View进行处理。
onTouchEvent()中对具体的触摸事件进行处理。
他们之间的关系可以用伪代码标示，如下：

public boolean dispatchTouchEvent(MotionEvent ev) {
    boolean consume = false;
    if (onInterceptTouchEvent(ev)) {
        consume = onTouchEvent(ev);
    } else {
        consume = child.dispatchTouchEvent(ev);
    }
    return consume;
}
另外，ViewGroup.onInterceptTouchEvent()默认返回false，即对触摸事件不进行拦截，都会分发到子View。

如果View设置了onTouchListener()，则onTouchListener()的处理在onTouchEvent()之前，如果onTouchListener()返回true，则View.onTouchEvent()不会被调用，即onTouchListener()的优先权高于onTouchEvent()

Android中默认认为View是消耗onTouchEvent()的，即返回值为true，除非它是不可点击的，即clickable和longClickable都为false。

更多参考资料
Android开发艺术探索-第三章 View的事件体系


####不要单纯的去想，要去做，脚踏实地的做
