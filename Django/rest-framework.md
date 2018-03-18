## 설치하기
```bash
pip install djangorestframework
```

## 세팅하기
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
    'myapp'
]

REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': ('rest_framework.permissions.IsAdminUser',),
    'PAGINATE_BY': 10
}
```

URL 추가
```python
from django.conf.urls import url, include
from rest_framework import routers
from animation import views

router = routers.DefaultRouter()
router.register(r'animations', views.AnimationViewSet)

urlpatterns = [
    path('admin/', admin.site.urls),
    url(r'^', include(router.urls)),
    url(r'^api-auth/', include('rest_framework.urls', namespace='rest_framework'))
]
```

animation/view.py
```python
from rest_framework import viewsets
from animation.serializers import AnimationSerializer
from animation.models import Animation

# Create your views here.

class AnimationViewSet(viewsets.ModelViewSet):
    queryset = Animation.objects.all()
    serializer_class = AnimationSerializer

```

animation/serializers.py
```python
from animation.models import Animation
from rest_framework import serializers

class AnimationSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Animation
        fields = ('title', 'number', 'year', 'quater', 'image', 'url')
```