# Daager2

## Gradle Setting
```gradle
// dagger2
implementation 'com.google.dagger:dagger:2.15'
annotationProcessor 'com.google.dagger:dagger-compiler:2.15'
implementation 'com.google.dagger:dagger-android:2.15'
implementation 'com.google.dagger:dagger-android-support:2.15'
annotationProcessor 'com.google.dagger:dagger-android-processor:2.15'
```

## Setting Error 해결
Dagger를 Precompile 해야하는데 안되는 문제가 발생하였다.
Kotlin을 사용하면서 이런 문제를 발생하였다.

```gradle
apply plugin: 'kotlin-kapt'
```
annotationProcessor 대신 kapt를 쓰면 해결된다.
```gradle
kapt 'com.google.dagger:dagger-compiler:2.15'
```