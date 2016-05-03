# eclipse 2 android studio  
my note for studying  
刚入职公司,公司的代码被前人写了一批又一批,有eclipse写的,有用h5写的,还有用c写的(ndk).  
而之前的代码全部都是eclipse开发的,我擅长的却是studio,而且是2.1的  
所以studio导入代码的时候遇到的问题太多了.  
   
   
 1.首先,需要将ndk配置好,因为之前没有使用过这个工具,所以必须下载并且配置  
   修改所有库的安卓版本和工程的安卓版本  
 2.修改project.properties文件,添加ndk的配置  
 android.useDeprecatedNdk=true  
 3.在luajava.c下自定义lua.h的目录  
 #include "../lua/lua.h"  
 #include "../lua/lualib.h"  
 #include "../lua/lauxlib.h"  
 4.导入第三方包(如v7的新版包等)  
 5.删除重复的dimen.xml文件  
 6.添加apache的网络访问库,在android{}中加入useLibrary 'org.apache.http.legacy'  
 7.UTF8和GBK的转码,最方便的就是复制文字直接到UTF8中  
 8.没有可扩展.9图片的改变(将其改为普通png)  
 9.找到所有不是png的图片改回其后缀  
 10.将过时的FloatMath改为Math  
 11.去掉其他库中多余的<category android:name="android.intent.category.LAUNCHER" /> 以防止出现多个app图标  
 12.notification的setlastesteventinfo用如下代码:  
 Notification.Builder builder = new Notification.Builder(MainActivity.this);  

                builder.setAutoCancel(false);
                builder.setTicker("this is ticker text");
                builder.setContentTitle("WhatsApp Notification");               
                builder.setContentText("You have a new message");
                builder.setSmallIcon(R.drawable.ic_launcher);
                builder.setContentIntent(pendingIntent);
                builder.setOngoing(true);
                builder.setSubText("This is subtext...");   //API level 16
                builder.setNumber(100);
                builder.build();

                myNotication = builder.getNotification();
                manager.notify(11, myNotication);
    
  完成这些步骤以后studio顺利运行此项目,后续还会继续对此进行更新 
