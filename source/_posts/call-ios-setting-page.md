---

title: iOS跳转到自己的权限设置页面
date: 2016-09-05 11:59:46

---


### 1. 跳转到自己的权限设置页面
当iOS App中需要的某种权限没有被授权的时候，需要引导用户手动打开]。通过以下代码可以跳转到系统设置里面本App的权限设置页面。
```
 if ([[UIApplication sharedApplication] canOpenURL:[NSURL URLWithString:UIApplicationOpenSettingsURLString]])
 {
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:UIApplicationOpenSettingsURLString]];
}
```

<!-- more -->
![示例图片](http://source.thinkcode.cn/post/img/call-setting-sample-pic.png)


如果App没有申请任何权限，将会跳转到“设置”首页。

### 2. 跳到指定的设置界面
iOS App可以跳转到指定的设置界面比如无线网络设置界面 蜂窝网络设置界面 定位设置界面等
首先需要设置URL Types，如下图

![示例图片](http://source.thinkcode.cn/post/img/call-setting-prefs-info.png)

然后通过以下代码就可以跳转到指定的设置页面了

```
if ([[UIApplication sharedApplication] canOpenURL:[NSURL URLWithString:@"指定设置项的url"]]) {
     [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"指定设置项的url"]];
}
```
比如跳转到定位服务：
```
[[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"prefs:root=LOCATION_SERVICES"]];
```
#### iOS 系统功能的 URL 汇总列表
>蜂窝网络：prefs:root=MOBILE_DATA_SETTINGS_ID
VPN — prefs:root=General&path=Network/VPN
Wi-Fi：prefs:root=WIFI
定位服务：prefs:root=LOCATION_SERVICES
个人热点：prefs:root=INTERNET_TETHERING
关于本机：prefs:root=General&path=About
辅助功能：prefs:root=General&path=ACCESSIBILITY
飞行模式：prefs:root=AIRPLANE_MODE
锁定：prefs:root=General&path=AUTOLOCK
亮度：prefs:root=Brightness
蓝牙：prefs:root=General&path=Bluetooth
时间设置：prefs:root=General&path=DATE_AND_TIME
FaceTime：prefs:root=FACETIME
设置：prefs:root=General
键盘设置：prefs:root=General&path=Keyboard
iCloud：prefs:root=CASTLE
iCloud备份：prefs:root=CASTLE&path=STORAGE_AND_BACKUP
语言：prefs:root=General&path=INTERNATIONAL
定位：prefs:root=LOCATION_SERVICES
音乐：prefs:root=MUSIC
Music Equalizer — prefs:root=MUSIC&path=EQ
Music Volume Limit — prefs:root=MUSIC&path=VolumeLimit
Network — prefs:root=General&path=Network
Nike + iPod — prefs:root=NIKE_PLUS_IPOD
Notes — prefs:root=NOTES
Notification — prefs:root=NOTIFICATIONS_ID
Phone — prefs:root=Phone
Photos — prefs:root=Photos
Profile — prefs:root=General&path=ManagedConfigurationList
Reset — prefs:root=General&path=Reset
Safari — prefs:root=Safari
Siri — prefs:root=General&path=Assistant
Sounds — prefs:root=Sounds
Software Update — prefs:root=General&path=SOFTWARE_UPDATE_LINK
Store — prefs:root=STORE
Twitter — prefs:root=TWITTER
Usage — prefs:root=General&path=USAGE
Wallpaper — prefs:root=Wallpaper

参考:
[Rejected 《iOS 跳转到设置界面》](http://www.jianshu.com/p/8e354e684e8a)