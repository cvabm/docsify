# 调试

## 无线调试

```

Android 手机需要是 Android 11 以上系统；开发者模式里有无线调试选项
电脑上的 Android SDK 工具需要 ≥ 30.0.0 版本，确认方式是：adb --version

1、打开无线调试- 使用配对码配对 - adb pair ip:port ，输入 code 码
2、adb connect ip:port(固定的 ip 和端口)
```

## 当前activity

```

```
adb shell dumpsys window | grep mCurrentFocus 获取当前页面
adb shell dumpsys activity activities | grep mResumedActivity

```