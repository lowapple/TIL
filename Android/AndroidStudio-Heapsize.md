# 이유
Mac에서 작업하기에는 heap size가 작음

# 해결
help -> edit custom vm option

```
-Xms2048m
-Xmx4096m
-XX:MaxPermSize=1024m
-XX:ReservedCodeCacheSize=768m
-XX:+UseCompressedOops
```