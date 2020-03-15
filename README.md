# flutter_errors_and_solutions
本仓库收集在flutter开发过程，遇到一些错误和如何解决的方案。

### Invalid `Podfile` file: no implicit conversion of nil into String.

ruby的版本过低，需要更新ruby版本。 [solution](https://www.cnblogs.com/doudouyoutang/p/10716376.html)


### 国际化不起作用

- 针对iOS需要在`Info.plist`添加`Localizations`配置项。 [solution](https://flutter.cn/docs/development/accessibility-and-localization/internationalization)

- 模拟器有效果，真机却没有效果。

需要在`LocalizationsDelegate`重写方法`isSupported`中添加具体语言代码。例如如果支持简体和繁体中文，模拟器只需要填写需要支持`zh`国家代码，但是在真机需要填写`zh_Hans`和`zh_Hant`。

### flutter upgrade很慢或卡住不动

- 在官网直接下载 [solution](https://flutter.dev/docs/get-started/install)

- 切换镜像

> 原本官方镜像

```
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

> 可切换清华大学镜像 
 [solution](https://mirror.tuna.tsinghua.edu.cn/help/dart-pub/)

```
$ PUB_HOSTED_URL="https://mirrors.tuna.tsinghua.edu.cn/dart-pub/" pub get # pub
$ PUB_HOSTED_URL="https://mirrors.tuna.tsinghua.edu.cn/dart-pub/" flutter packages get # flutter
```


### Waiting for another flutter command to release the startup lock

- 有可能同时多个命令执行编译（flutter环境build，或在iOS和android环境同时对同一个工程文件执行编译）。

```
1.打开flutter的安装目录/bin/cache/；
2.删除lockfile文件。

或

暂停一方环境编译。
```




