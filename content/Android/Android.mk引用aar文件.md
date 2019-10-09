---
title: "Android.mk引用aar文件"
date: 2018-12-11 14:16
---

# Android 5.0及以上版本

* 修改Android.mk文件 
```
# 1. 
LOCAL_AAPT_FLAGS := \
  --auto-add-overlay \
  --extra-packages <aar package>
# 2.
LOCAL_STATIC_JAVA_AAR_LIBRARIES := <aar alias>

# 3. 
LOCAL_PREBUILT_STATIC_JAVA_LIBRARIES := <aar alias>:libs/<lib file>.aar
```


----------

# Android 5.0以下版本

* 解压aar文件
```
unzip <aar file>
```

* 修改Android.mk文件

```
# 1. 
LOCAL_AAPT_FLAGS := \
  --auto-add-overlay \
  --extra-packages <aar package>
# 2.
LOCAL_RESOURCE_DIR := $(LOCAL_PATH)/res \
    $(LOCAL_PATH)/<aar dir>/res

# 3. 
LOCAL_STATIC_JAVA_LIBRARIES := <aar alias>

# 4. 
LOCAL_PREBUILT_STATIC_JAVA_LIBRARIES := <aar alias>:<aar dir>/classes.jar
```

# 参考
[Android.mk引用aar文件][1]


  [1]: https://blog.csdn.net/xiaowan0404/article/details/52166969 "Android.mk引用aar文件"
