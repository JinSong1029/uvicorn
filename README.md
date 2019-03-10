**Requirements**: Python 3.5, 3.6, 3.7

Uvicorn server.

## Quickstart

Install using `pip`:

```shell
$ pip install uvicorn
```

Create an application, in `app.py`:

```python
class App():
    def __init__(self, scope):
        assert scope['type'] == 'http'
        self.scope = scope

    async def __call__(self, receive, send):
        await send({
            'type': 'http.response.start',
            'status': 200,
            'headers': [
                [b'content-type', b'text/plain'],
            ],
        })
        await send({
            'type': 'http.response.body',
            'body': b'Hello, world!',
        })
```

Run the server:

```shell
$ uvicorn app:App
```

---

<p align="center"><i>Uvicorn is <a href="https://github.com/encode/uvicorn/blob/master/LICENSE.md">BSD licensed</a> code.<br/>Designed & built in Brighton, England.</i><br/>&mdash; 🦄  &mdash;</p>

[uvloop]: https://github.com/MagicStack/uvloop
[httptools]: https://github.com/MagicStack/httptools
[asgi]: https://github.com/django/asgiref/blob/master/specs/asgi.rst
