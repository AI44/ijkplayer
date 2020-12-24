## 编译要点

##### 一、./android/contrib/tools/do-compile-openssl.sh和do-compile-ffmpeg.sh

export PATH=$FF_TOOLCHAIN_PATH/bin:$PATH 改为 export PATH="$FF_TOOLCHAIN_PATH/bin:$PATH"

##### 二、./android/contrib/tools/do-detect-env.sh

11*|12*|13*|14*) 改为 11*|12*|13*|14*|21*) 根据ndk版本而定

##### 三、./android/ijkplayer/ijkplayer-armv7a/src/main/jni/ijkmedia 需要重定向到 ./ijkmedia（根据自己目录进行修改）

```
sudo ln -s $LINUX/ijkplayer/ijkmedia $LINUX/ijkplayer/android/ijkplayer/ijkplayer-armv7a/src/main/jni
或
sudo ln -s $LINUX/ijkplayer-k0.8.8/ijkmedia $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-armv7a/src/main/jni
或
sudo ln -s $LINUX/ijkplayer-k0.8.8/ijkmedia $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-x86/src/main/jni
或
sudo ln -s $LINUX/ijkplayer-k0.8.8/ijkmedia $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-arm64/src/main/jni
```

四、重定向x86 Android.mk文件

```
sudo ln -s $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-armv7a/src/main/jni/Android.mk $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-x86/src/main/jni
或
sudo ln -s $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-armv7a/src/main/jni/Android.mk $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-arm64/src/main/jni
sudo ln -s $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-armv7a/src/main/jni/ffmpeg $LINUX/ijkplayer-k0.8.8/android/ijkplayer/ijkplayer-arm64/src/main/jni
```



## 编译指令

```
#./init-android.sh
#./init-android-openssl.sh
#用打包好的代码不需要以上步骤

cd android/contrib

./compile-openssl.sh clean
./compile-ffmpeg.sh clean

./compile-openssl.sh armv7a
./compile-ffmpeg.sh armv7a

cd ..

./compile-ijk.sh clean
./compile-ijk.sh armv7a
```