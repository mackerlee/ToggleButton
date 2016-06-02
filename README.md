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
      
      //--用方式二触发响应
      <ToggleButton
        android:id="@+id/togglebutton02"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/togglebutton01"
        android:textOn="开"
        android:textOff="关"/>
    //--滑动开关组件
    <Switch
        android:id="@+id/switch01"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/togglebutton02"
        android:textOn="开"
        android:textOff="关"
        //--switch响应方法
        android:onClick="onSwitchClicked"/>
  </RelativeLayout>
  
  在app->java->包名->MainActivity.java中设置响应方法：
  package com.example.mackerlee.android_56;

  import android.support.v7.app.AppCompatActivity;
  import android.os.Bundle;
  import android.view.View;
  import android.widget.CompoundButton;
  import android.widget.Switch;
  import android.widget.Toast;
  import android.widget.ToggleButton;
  
  public class MainActivity extends AppCompatActivity {
  
      private ToggleButton tb1,tb2;
      private Switch sw1;
      @Override
      protected void onCreate(Bundle savedInstanceState) {
          super.onCreate(savedInstanceState);
          setContentView(R.layout.activity_main);
          tb1 = (ToggleButton)findViewById(R.id.togglebutton01);
  
          //--ToggleButton响应事件方式二
          tb2 = (ToggleButton) findViewById(R.id.togglebutton02);
          tb2.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
              public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
                  switch (buttonView.getId()){
                      case R.id.togglebutton02:
                          if (isChecked) {
                              Toast.makeText(MainActivity.this,"方式二灯已经打开",Toast.LENGTH_LONG).show();
                          } else {
                              Toast.makeText(MainActivity.this,"方式二灯已经关闭",Toast.LENGTH_LONG).show();
                          }
                          break;
                      default:
                          break;
                  }
              }
          });
  
          sw1 = (Switch)findViewById(R.id.switch01);
      }
  
      //--ToggleButton事件响应方法一：在配置文件中设置响应函数
      public void onToggleClicked(View view) {
          // Is the toggle on?
          boolean on = ((ToggleButton) view).isChecked();
  
          if (on) {
              Toast.makeText(this,"方式一灯已经打开",Toast.LENGTH_LONG).show();
          } else {
              Toast.makeText(this,"方式一灯已经关闭",Toast.LENGTH_LONG).show();
          }
      }
  
      //--Switch事件响应：在配置文件中设置响应函数
      public void onSwitchClicked(View view) {
          // Is the toggle on?
          boolean on = ((Switch) view).isChecked();
  
          if (on) {
              Toast.makeText(this,"滑动开关灯已经打开",Toast.LENGTH_LONG).show();
          } else {
              Toast.makeText(this,"滑动开关灯已经关闭",Toast.LENGTH_LONG).show();
          }
      }
  }
