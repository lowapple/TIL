## 어플리케이션 만들기

```bash
python manage.py startapp blog
```

생성 후 사용한다고 Django에 알려주기

```bash
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog', <= 추가
]
```

Blog라는 모델을 작성
```python
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey('auth.User', on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(
            default=timezone.now)
    published_date = models.DateTimeField(
            blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```

## Field Type

Field Type | 설명
|--|--|
CharField | 제한된 문자열 필드 타입. 최대 길이를 max_length 옵션에 지정해야 한다. 문자열의 특별한 용도에 따라 CharField의 파생클래스로서, 이메일 주소를 체크를 하는 EmailField, IP 주소를 체크를 하는 GenericIPAddressField, 콤마로 정수를 분리한 CommaSeparatedIntegerField, 특정 폴더의 파일 패스를 표현하는 FilePathField, URL을 표현하는 URLField 등이 있다.
TextField | 대용량 문자열을 갖는 필드
IntegerField | 32 비트 정수형 필드. 정수 사이즈에 따라 BigIntegerField, SmallIntegerField 을 사용할 수도 있다.
BooleanField | true/false 필드. Null 을 허용하기 위해서는 NullBooleanField를 사용한다.
DateTimeField | 날짜와 시간을 갖는 필드. 날짜만 가질 경우는 DateField, 시간만 가질 경우는 TimeField를 사용한다.
DecimalField | 소숫점을 갖는 decimal 필드
BinaryField | 바이너리 데이타를 저장하는 필드
FileField | 파일 업로드 필드
ImageField | FileField의 파생클래스로서 이미지 파일인지 체크한다.
UUIDField | GUID (UUID)를 저장하는 필드

## 테이블 만들기

변화가 생겼다는 것을 말함
```bash
python manage.py makemigrations blog
```

반영할 수 있도록 되면
반영할 수 있음

``bash
python manage.py migrate blog
```