---
title: "Android Studio Guide"
permalink: /docs/android-studio-guide/
excerpt: "How to create a bangtal library game (Android App) using Android Studio."
modified: "2021-02-14 18:11:00 +0900"
---
Android Studio를 사용해서 방탈 라이브러리 게임(안드로이드 앱)을 만들 수 있다.

## Android Studio 설치하기
먼저 최신 버전의 [Android Studio](https://developer.android.com/studio)를 다운 받아서 설치한다.
- C/C++ 개발을 위해서 NDK를 설치해야 한다.

<figure>
  <a href="/images/android_studio_install.png">
  <img src="/images/android_studio_install.png" alt="Android Studio SDK Manager"></a>
</figure>

## Bangtal Library 설치하기
최신 버전의 방탈 라이브러리([Bangtal.msi](https://github.com/bosornd/bangtal/releases))를 설치한다.

## 프로젝트 생성하기
Android Studio에서 "Native C++"프로젝트를 생성한다.
<figure>
  <a href="/images/android_studio_create_project1.png">
  <img src="/images/android_studio_create_project1.png" alt="프로젝트 생성하기1"></a>
</figure>
<figure>
  <a href="/images/android_studio_create_project2.png">
  <img src="/images/android_studio_create_project2.png" alt="프로젝트 생성하기2"></a>
</figure>
<figure>
  <a href="/images/android_studio_create_project3.png">
  <img src="/images/android_studio_create_project3.png" alt="프로젝트 생성하기3"></a>
</figure>

## 프로젝트 설정하기
- app/build.gradle의 dependencies에 다음을 추가합니다. 방탈 라이브러리를 포함하도록 설정합니다.

```
debugImplementation fileTree(dir: System.getenv('BANGTAL_HOME') + '/lib/android/debug', include: ['*.aar'])
releaseImplementation fileTree(dir: System.getenv('BANGTAL_HOME') + '/lib/android/release', include: ['*.aar'])
```

- app/src/main/cpp/CMakeLists.txt에 다음을 추가합니다. 헤더/라이브러리 경로를 설정합니다.

```
target_include_directories(native-lib PUBLIC $ENV{BANGTAL_HOME}/include/)
target_link_libraries(native-lib $ENV{BANGTAL_HOME}/lib/android/${CMAKE_BUILD_TYPE}/${CMAKE_ANDROID_ARCH_ABI}/libBangtal.so)
```

- app/src/main/AndroidManifest.xml을 다음과 같이 수정합니다.

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.bosornd.example">

    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-feature android:glEsVersion="0x00020000" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round">
        <activity
            android:name="com.bosornd.bangtal.AppActivity"
            android:screenOrientation="landscape"
            android:configChanges="orientation|keyboardHidden|screenSize"
            android:label="@string/app_name"
            android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
            android:launchMode="singleTask"
            android:taskAffinity="">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```
&lt;uses&gt;를 추가하고, &lt;activity&gt;를 교체하면 됩니다.

## 게임 프로그램 만들기
장면을 생성(createScene 함수)하고, 생성된 장면으로 게임을 시작(startGame 함수)해 본다.
프로그램은 app/src/main/cpp/native-lib.cpp에 작성하면 됩니다.

## 에셋 추가하기
게임에 사용되는 이미지 등의 리소스는 app/src/main/assets 폴더에 넣으면 됩니다.

<figure>
  <a href="/images/android_studio_create_assets.png">
  <img src="/images/android_studio_create_assets.png" alt="에셋 폴더 만들기"></a>
</figure>

## 주의할 점
- 라이브러리 이름(native-lib)을 바꾸면 안됩니다. 방탈 라이브러리에서 사용합니다.
- 안드로이드에서는 main() 함수가 종료된 다음에 게임이 시작됩니다.
main() 함수의 지역 변수가 소멸되므로 람다 함수에서 사용하면 안됩니다.

## 참고
- [https://github.com/bosornd/bangtal.android](https://github.com/bosornd/bangtal.android)
- [https://github.com/bosornd/bangtal.c](https://github.com/bosornd/bangtal.c)
- [https://github.com/bosornd/bangtal.cpp](https://github.com/bosornd/bangtal.cpp)
- [https://github.com/bosornd/bangtal.gogh](https://github.com/bosornd/bangtal.gogh)
- [https://github.com/bosornd/bangtal.othello](https://github.com/bosornd/bangtal.othello)
