# UIButton 이미지 사이즈 줄이기
## 문제

CheckBox를 제작하면서 이미지를 UIButton에 넣었는데 이미지 사이즈가 작았다.
이 이미지를 키우기 위해서는 간단하게 함수로 제공되지 않고 개발자가 직접 코딩해서 건드려야 한다... 이 문제를 해결하기 위해 여러 사이트에 돌아다니면서 삽질을 하였다.

## 해결
```swift
func resizeImage(image : UIImage, width : Float, height : Float) -> UIImage? {
    
    let cgWidth = CGFloat(width)
    let cgHeight = CGFloat(height)
    
    // Begine Context
    UIGraphicsBeginImageContext(CGSize(width: cgWidth, height: cgHeight))
    // Get Current Context
    let context = UIGraphicsGetCurrentContext()
    context?.translateBy(x : 0.0, y : cgHeight)
    context?.scaleBy(x: 1.0, y: -1.0)
    context?.draw(image.cgImage!, in: CGRect(x: 0.0, y: 0.0, width: cgWidth, height: cgHeight))
    let scaledImage : UIImage? = UIGraphicsGetImageFromCurrentImageContext()
    // End Context
    UIGraphicsEndImageContext()
    
    if (scaledImage != nil) {
        return scaledImage
    }
    else {
        return nil
    }
}
```
사용
```swift
self.setImage(self.resizeImage(image: self.checkedImage, width: 16, height: 16), for: UIControlState.normal)
```

## 참고
http://pds0819.tistory.com/entry/iphone-UIButton-내-image-size-줄이는-방법

https://iosdevcenters.blogspot.com/2015/12/how-to-resize-image-in-swift-in-ios.html