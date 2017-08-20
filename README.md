# Mac-environment-react-native
### mac下run-ios环境配置bug解决
在安装好xcode之后，用react-native-cli生成了demo，本以为应该很顺利能run-ios版本，结果出毛病了。
```
Failed to install the requested application
An application bundle was not found at the provided path.
Provide a valid path to the desired application bundle.
Print: Entry, ":CFBundleIdentifier", Does Not Exist

Command failed: /usr/libexec/PlistBuddy -c Print:CFBundleIdentifier build/Build/Products/Debug-iphonesimulator/ReactNativexx.app/Info.plist
Print: Entry, ":CFBundleIdentifier", Does Not Exist

```
#### 解决办法
- 首先删除node_modules
- 修改package.json中react-native的版本为0.44.3 react为16.0.0-alpha.6
- npm install
- react-native run-ios
- done

### mac下run-android环境配置bug解决
**bug code**
```
Android-sdk is not found
```
这里有点特殊，我的的android-sdk环境变量应该是配置好的，终端adb也能输出内容，但一直报错。附上整个流程
#### Android-sdk基础搭建
 首先下载android studio安装好 http://reactnative.cn/docs/0.47/getting-started.html 相关的sdk版本安装好
##### 环境配置
 - 进入终端-->sudo su-->open .bash_profile
 - 粘贴地址如下
 ```
  export ANDROID_HOME=/Users/mac/Library/Android/sdk
  export PATH=${PATH}:${ANDROID_HOME}/tools  
  export PATH=${PATH}:${ANDROID_HOME}/platform-tools
  GRADLE_HOME=/Applications/Android\ Studio.app/Contents/gradle/gradle-3.2/bin;
  export PATH=$PATH:$GRADLE_HOME/bin
``` 
 - 上述的地址获去的方法  Android Studio 打开 有个sdk设置 可以看到sdk地址 复制粘贴到ANDROID_HOME的地址
 gradle配置为Android Studio的上一个目录 注意Android Studio 有空格 需要转义
- 使配置生效 source ~/.bash_profile
- 模拟器使用
Genymotion
 安装完成之后，添加一个Android 6‘0的版本，在外面sdk的选项中，选择Android studio的sdk地址
- 至此  进入demo下  react-native run-android  模拟器出现欢迎界面

