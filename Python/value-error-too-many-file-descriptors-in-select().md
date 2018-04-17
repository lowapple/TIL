# 배경
웹 데이터 크롤링을 하다가 만난 에러이다.

>  too many file descriptors in select()

Windows의 asyncio루프에서는 기본적으로 64개의 소캣 만 사용할 수 있기 때문에 이 문제가 발생하는 것이다.

[ProactorEventLoop](https://docs.python.org/3/library/asyncio-eventloops.html#asyncio.ProactorEventLoop) 를 사용하면 이 문제를 해결할 수 있다.

# 해결
```python
import asyncio, sys

if sys.platform == 'win32':
    loop = asyncio.ProactorEventLoop()
    asyncio.set_event_loop(loop)

loop = asyncio.get_event_loop()
loop.run_until_complete(crawler.main())
```