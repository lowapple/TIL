# Status bar size 구하기

기본적인 값은 20이다.
하지만 여러가지 요인으로 바뀌는 경우가 있다.

```swift
let statusBar : CGRect = UIApplication.shared.statusBarFrame
```