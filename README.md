# TT
BaseAdapter使用步骤
  1,创建一个类继承BaseAdapter
  2,创建构造方法
  3,修改getCount()方法返回值为list.size()
  4,修改getItem()方法返回值为list.get(position);
  5,修改getItemId返回值为position
  6,重写getView()方法，设置item内容
