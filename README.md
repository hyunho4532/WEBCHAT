# WEBCHAT
사람들과 소통할 수 있는 ChatRoom!

<br>

### 하 프로젝트 인코딩 문제로 new-source 브랜치로 변경

1. 루트 디렉토리에 .env 파일 만든 후 아래 코드 복붙

```
CHANNEL_LAYER_REDIS_URL=redis://:redis-password@redis-endpoint:redis-port
```

<br>

2. 루트 디렉토리에 run_test_hello_channel.py 파일 만든 후 아래 코드 복붙

```
import asyncio
import os

import django
from channels.layers import get_channel_layer

os.environ["DJANGO_SETTINGS_MODULE"] = "mysite.settings"
django.setup()


async def main():

    channel_layer = get_channel_layer()
    message_dict = { 'content': 'world' }

    await channel_layer.send('hello', message_dict)

    response_dict = await channel_layer.receive('hello')
    is_equal = message_dict == response_dict
    print("송신 / 수신 데이터가 같습니까?", is_equal)


asyncio.run(main())
```
