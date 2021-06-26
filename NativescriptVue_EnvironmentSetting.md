## Set up for nativescript-vue / macOS + Android

<!-- うごかなくなったら、ctrl+C -->

はじめはターミナルで

# install nativescript

https://nativescript-vue.org/en/docs/getting-started/installation/
`npm install -g nativescript`

# create new project

https://nativescript-vue.org/en/docs/getting-started/quick-start/
`ns create <project-name> --vue # add --ts if you'd like to scaffold a project with TypeScript`

ここから VSCode 上で、作ったファイルを開いた状態で

```
cd <project-name>
npm install
ns run
```

# macOS + Android

https://docs.nativescript.org/environment-setup.html#macos-android
// sudo をつけないと、error: cannot open .git/FETCH_HEAD: Permission denied になる
sudo git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core fetch --unshall
とても時間がかかるが、辛抱強く待つ。やらないと永遠に clone ホニャホニャとで続けて、先に進めない

```
brew tap AdoptOpenJDK/openjdk
brew install --cask adoptopenjdk15
```

エラーになる場合

```
Error: Download failed on Cask 'adoptopenjdk15' with message: No such file or directory @ dir_s_rmdir - /usr/local/var/homebrew/locks/0e366ed7d2f446b4147b7d3d5e56c8f73f5d80f8b52b5e9831e68029090ff5a5--OpenJDK15U-jdk_x64_mac_hotspot_15.0.2_7.pkg.incomplete.lock
```

↓（代替案｝adoptopenjdk の公式サイトより、.pkg ダウンロード、インストール
https://adoptopenjdk.net/index.html?variant=openjdk15&jvmVariant=hotspot
で、OpenJDK15 をダウンロード、インストールする

https://developer.android.com/studio
Android Studio をダウンロードして、インストールする

export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:\$ANDROID_HOME/platform-tools
npm install -g nativescript

ns doctor android

<!-- Component @nativescript/android is not installed.でる。。。。 -->

JDK 自体がそもそも入ってないらしいので、ここの「Install the Coding Pack for Java」でインストール
https://code.visualstudio.com/docs/java/java-tutorial

ns doctor android すると途中で homebrew が permission denied だよと泣くので、[ここ](https://stackoverflow.com/questions/16432071/how-to-fix-homebrew-permissions)の Big Sur 以降のやり方で

```
$ sudo chown -R $(whoami) $(brew --prefix)/*
```

をするものの、`sudo`のパスワード聞かれないんだけどだいじょぶなのか？

```
nn@Vallum nm-recipes-mobile % brew --version
Homebrew 3.2.0
Homebrew/homebrew-core (git revision 5da7097ab0; last commit 2021-05-07)
Homebrew/homebrew-cask (git revision c611d7befe; last commit 2021-06-26)
```

その後もう一度`ns doctor android`やると homebrew のところでつまらなくなった。super user のパスワードが聞かれるようになった。

Step 2

```

Set ANDROID_HOME=/usr/local/share/android-sdk
Set ANDROID_SDK_ROOT=/usr/local/share/android-sdk
Configuring your system for Android development... This might take some time, please, be patient.
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: There seem to be some problems with the Android configuration
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: There seem to be some problems with the Android configuration
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: There seem to be some problems with the Android configuration
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: There seem to be some problems with the Android configuration
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: There seem to be some problems with the Android configuration
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: There seem to be some problems with the Android configuration
```

いつも起きるらしい。
Step 4

```
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
sudo: /usr/local/share/android-sdk/extras/intel/Hardware_Accelerated_Execution_Manager/silent_install.sh: command not found
WARNING: Failed to install Intel HAXM.
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:73)
        at com.android.sdklib.tool.sdkmanager.SdkManagerCli.main(SdkManagerCli.java:48)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
```

全然うまくいきませんね

STEP 5

```
Do you want to create Android emulator? (y/n)
y
Exception in thread "main" java.lang.NoClassDefFoundError: javax/xml/bind/annotation/XmlSchema
        at com.android.repository.api.SchemaModule$SchemaModuleVersion.<init>(SchemaModule.java:156)
        at com.android.repository.api.SchemaModule.<init>(SchemaModule.java:75)
        at com.android.sdklib.repository.AndroidSdkHandler.<clinit>(AndroidSdkHandler.java:81)
        at com.android.sdklib.tool.AvdManagerCli.run(AvdManagerCli.java:213)
        at com.android.sdklib.tool.AvdManagerCli.main(AvdManagerCli.java:200)
Caused by: java.lang.ClassNotFoundException: javax.xml.bind.annotation.XmlSchema
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:606)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:168)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 5 more
WARNING: Failed to create Android emulator.
```

OpenJDK は正しく１５が入っているっぽい

```
nn@Vallum nm-recipes-mobile % java --version
openjdk 15.0.2 2021-01-19
OpenJDK Runtime Environment AdoptOpenJDK (build 15.0.2+7)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 15.0.2+7, mixed mode, sharing)
```

> Add the following lines to your shell profile, usually ~/.bash_profile or ~/.bashrc, or if you are using zsh then ~/.zprofile or ~/.zshrc config file:
> とあるが、どうもよくわからん内容が`.zprofile`に書いてあったので退避させてコピペ：

```
export JAVA_HOME=/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home
export ANDROID_HOME=/usr/local/share/android-sdk
export ANDROID_SDK_ROOT=/usr/local/share/android-sdk
```

を

```
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

にした。すると`ns doctor android`が`✖ Component @nativescript/android is not installed.`のところで止まるようになった。
`$ npm install -g @nativescript/android`するとそれ自体はうまくいく(`+ @nativescript/android@8.0.0`)。
しかしもう一度`ns doctor android`しても同じところで止まる。`tns platform add android`すると問題なくなった
