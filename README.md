1、linux应用
```
参考附件Rockchip_Developer_Guide_Linux_WIFI_BT_CN.pdf
https://docs.qq.com/doc/p/a9dd00348639929fc080d20dbbdc4feea89c4983

运行./usr/bin/rkwifibt_app_test BT 测试

RKWIFIBT_APP_V1.6.3.rar附件是新的bluez5.77的补丁和应用

删除这两个目录
rm buildroot/package/bluez5_utils/* -rf
rm buildroot/package/bluez-alsa/* -rf

替换附件buildroot/package 下的编译目录
编译的时候会自动打上patch不用自己添加

kernel的patch需要自己手动添加，
kernel代码补丁：
根据对应kernel的版本，打上对应补丁
！！！切记：以上修改完成后，全部clean，重新编译。


里面还有include、test目录和库
对比external/rkwifibt-app 是否一致
不一致就替换

```
2、使用bluetoothctl工具
```
针对rkwfibt_app 我们对bluez5做了定制化，与bluetoothctl冲突。
如果这边用传统bluetoothctl工具连接，需要去掉我们buildroot自带的bluez补丁
还要加上buildroot蓝牙电话验证.7z的补丁才能正常使用
```
