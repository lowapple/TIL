비동기로 동작하는 Http 모듈이다.

### install
```
pip install asyncio
pip install aiohttp
pip install cchardet
pip install aiodns
```

Example
```python
import aiohttp
import asyncio
import async_timeout

async def fetch(session, url):
    async with async_timeout.timeout(10):
        async with session.get(url) as response:
            return await response.text()

async def main():
    async with aiohttp.ClientSession() as session:
        html = await fetch(session, 'http://python.org')
        print(html)

loop = asyncio.get_event_loop()
loop.run_until_complete(main())
```

```python
from concurrent.futures import ALL_COMPLETED

# 한번에 완료 후 결과 제출
data_tasks = [asyncio.ensure_future(get_data(i)) for i in range(0, 50)]
completed, pending = await asyncio.wait(tasks, return_when=ALL_COMPLETED)

print(completed)
```

다른 방법
```python
data_tasks = [asyncio.ensure_future(get_data(i)) for i in range(0, 50)]
result = asyncio.gather(*data_tasks)

print(result)
```