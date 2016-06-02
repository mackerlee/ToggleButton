# ToggleButton

android 56 lesson
1.ToggleButton开关按钮：一个切换按钮，允许用户改变两个状态之间的设置.
2.Switche滑动选择开关：与ToggleButton功能类似，android4.0后新增的滑动开关控件.
3.ToggleButton实例：在res->layout->activity_main.xml中：
  <?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:paddingBottom="@dimen/activity_vertical_margin"
      android:paddingLeft="@dimen/activity_horizontal_margin"
      android:paddingRight="@dimen/activity_horizontal_margin"
      android:paddingTop="@dimen/activity_vertical_margin"
      tools:context="com.example.mackerlee.android_56.MainActivity">
  
      <ToggleButton
          android:id="@+id/togglebutton01"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          //--开关打开的显示文本内容
          android:textOn="开"
          android:textOff="关"
          //--开关的响应事件
          android:onClick="onToggleClicked"/>
  </RelativeLayout>
  
  在app->java->包名->MainActivity.java中设置响应方法：
  package com.example.mackerlee.android_56;

  import android.support.v7.app.AppCompatActivity;
  import android.os.Bundle;
  import android.view.View;
  import android.widget.Toast;
  import android.widget.ToggleButton;
  
  public class MainActivity extends AppCompatActivity {
  
      private ToggleButton tb;
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
          tb = (ToggleButton)findViewById(R.id.togglebutton01);
  
      }
  
      //--ToggleButton事件响应方法一：在配置文件中设置响应函数
      public void onToggleClicked(View view) {
          // Is the toggle on?
          boolean on = ((ToggleButton) view).isChecked();
  
          if (on) {
              Toast.makeText(this,"灯已经打开",Toast.LENGTH_LONG).show();
          } else {
              Toast.makeText(this,"灯已经关闭",Toast.LENGTH_LONG).show();
          }
      }
  }

