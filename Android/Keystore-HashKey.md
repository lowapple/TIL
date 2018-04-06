# 문제 발생
FacebookSDK와 KakaoSDK를 사용하기 위해서 해당 앱의 HashKey를 얻어서 등록하고, 사용해야한다.
앱을 출시한 후 Facebook과 Kakao 로그인 기능이 작동을 안한다는 피드백을 받았다.

# 문제 원인
Google에서 지원하는 [앱 서명 키 관리](https://support.google.com/googleplay/android-developer/answer/7384423?hl=ko) 기능으로 인해 앱의 HashKey가 달라진 것이다.

# 문제 해결
Stackoverflow를 [참고](https://stackoverflow.com/questions/44355452/google-play-app-signing-key-hash/44448437#44448437)하여 해결할 수 있었다.

1. GooglePlayConsole -> 출시관리 -> 앱 서명
2. 앱 서명 인증서 SHA-1 인증서를 복사한다. ex ) **8A:CF:6C:08:D4:84:1D:77:D7:37:13:4C:BD:56:55:73:26:4D:79:E7**
3. 터미널을 실행한 뒤
~~~
echo 8A:CF:6C:08:D4:84:1D:77:D7:37:13:4C:BD:56:55:73:26:4D:79:E7 | xxd -r -p | openssl base64
~~~
~~~is9sCNSEHXfXNxNMvVZVcyZNeec=
~~~

해당 HashKey를 Facebook과 Kakao 개발자 페이지에 등록하면 해결된다.