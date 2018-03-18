## 프로젝트 생성

```bash
mkdir djangoproject
cd djangoproject

python3 -m venv myproject
```

## 가상환경 실행

```bash
myproject\Scripts\activate
```

## 장고 설치

```bash
pip install django
```

## 장고 세팅

```bash
django-admin startproject myproject .
```


#### setting에서 변경
```python
 TIME_ZONE = 'Asia/Seoul'
```

```python
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```


#### 데이터 베이스 설정
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

#### 데이터 베이스 생성
```bash
python manage.py migrate
```

## 실행
``` bash
python manage.py runserver
```