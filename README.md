# DavidDatePickerDemo
【Android】时间选择器，选择日期DatePicker 简单详解demo及教程

作者：程序员小冰，GitHub主页：https://github.com/QQ986945193 

新浪微博：http://weibo.com/mcxiaobing 

首先给大家看一下我们今天这个最终实现的效果图： 

这个是安卓4.x系统是这个样式的。滚动那是手动选择日期的。其他系统是另一种效果。

![这里写图片描述](http://plblqapuw.bkt.clouddn.com/DavidDatePickerDemo.gif)

这个比较简单，具体效果UI图以及时间显示样式，大家可以自己修改。

总体来说，这个效果实现起来还是比较简单的，我相信你能够移植到自己的项目中。

布局比较简单，就有一个button以及textview。所以我就先放java实现代码吧：

```
package daviddatepickerdemo.qq986945193.com.daviddatepickerdemo;


import java.util.Calendar;

import android.app.Activity;
import android.app.DatePickerDialog;
import android.app.Dialog;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.DatePicker;
import android.widget.TextView;
/**
 * @author ：程序员小冰
 * @新浪微博 ：http://weibo.com/mcxiaobing
 * @GitHub: https://github.com/QQ986945193
 * @CSDN博客: http://blog.csdn.net/qq_21376985
 * @码云OsChina ：http://git.oschina.net/MCXIAOBING
 */

/**
 * 时间选择器
 */
public class MainActivity extends Activity {
    int mYear, mMonth, mDay;
    Button btn;
    TextView dateDisplay;
    final int DATE_DIALOG = 1;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btn = (Button) findViewById(R.id.dateChoose);
        dateDisplay = (TextView) findViewById(R.id.dateDisplay);

        btn.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View v) {
                showDialog(DATE_DIALOG);
            }
        });

        final Calendar ca = Calendar.getInstance();
        mYear = ca.get(Calendar.YEAR);
        mMonth = ca.get(Calendar.MONTH);
        mDay = ca.get(Calendar.DAY_OF_MONTH);
    }

    @Override
    protected Dialog onCreateDialog(int id) {
        switch (id) {
            case DATE_DIALOG:
                return new DatePickerDialog(this, mdateListener, mYear, mMonth, mDay);
        }
        return null;
    }

    /**
     * 设置日期 利用StringBuffer追加
     */
    public void display() {
        dateDisplay.setText(new StringBuffer().append(mMonth + 1).append("-").append(mDay).append("-").append(mYear).append(" "));
    }

    private DatePickerDialog.OnDateSetListener mdateListener = new DatePickerDialog.OnDateSetListener() {

        @Override
        public void onDateSet(DatePicker view, int year, int monthOfYear,
                              int dayOfMonth) {
            mYear = year;
            mMonth = monthOfYear;
            mDay = dayOfMonth;
            display();
        }
    };
}
```
xml布局文件代码如下：

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:gravity="center"
    android:orientation="vertical">

    <TextView
        android:id="@+id/dateDisplay"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="我是默认时间显示"/>

    <Button
        android:id="@+id/dateChoose"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="选择日期" />
</LinearLayout>

```
最后直接运行即可看到上面的效果。如果对您有帮助，欢迎star，fork。。。

当然如果我的项目帮到了你，欢迎进行打赏，请作者喝杯茶。谢谢支持。

![支付宝](http://plblqapuw.bkt.clouddn.com/alipay.jpg =200x300)

![微信](http://plblqapuw.bkt.clouddn.com/wechat.png =200x300)

