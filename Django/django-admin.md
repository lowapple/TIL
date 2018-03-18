## 관리자

등록
```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

관리자 생성
```bash
python manage.py createsuperuser
```