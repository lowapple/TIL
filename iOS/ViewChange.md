# iOS 뷰 변경방법

가장 기본적인 View변경 방법
```swift
if let storyboard : UIStoryboard = UIStoryboard(name: "Main", bundle: nil) {
    if let view : UIViewController = storyboard.instantiateViewController(withIdentifier: "HomeViewController") {
        // self.navigationController?.setViewControllers([view], animated: true)
        self.present(view, animated: true, completion: nil)
    }
}
```

Storyboard를 여러개 생성해서 작업할 때
class 이름과 Storyboard의 이름을 같게 한 후 작업한다.

```
View
    Controller
        HomeViewController.swift
    Storyboard
        HomeViewController.storyboard
```

```swift
// HomeViewController.swift

extension NSObject {
    static func classNameToString() -> String {
        return String(reflecting: self).components(separatedBy: ".").last!
    }
    func classNameToString() -> String {
        return String(reflecting: self).components(separatedBy: ".").last!
    }
}

class HomeViewController : UIViewController {

    ...

    static func storyboardInstance() -> HomeViewController? {
        let storyboard = UIStoryboard(name: classNameToString(), bundle: nil)
        return storyboard.instantiateInitialViewController() as? HomeViewController
    }
}
```

```swift
// 호출시
if let signupView = HomeViewController.storyboardInstance() {
    navigationController?.pushViewController(signupView, animated: true)
}
```
이처럼 간단하게 표현할 수 있다.

Storyboard를 많이 만드는 경우 BaseView를 하나 만들어 그 안에 만들어두고 상속해서 쓰는것이 좋다.