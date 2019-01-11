### httpretty
---
https://github.com/gabrielfalcao/HTTPretty

```
pip install httpretty
```

```py
import sure
import httpretty
import requests
@httpretty.activate
def test_httpbin():
  httpretty.register_uri(
    httpretty.GET,
    "https://httpbin.org/ip",
    body='{"origin": "127.0.0.1"}'
  )
  response = requests.get('https://httpbin.org/ip')
  response.json().should.equal({'origin': '127.0.0.1'})
  httpretty.latest_requests().should.have.length_of(1)
  httpretty.last_request().should.equal(httpretty.latest_requests()[0])
  httpretty.last_request().body.should.equal('{"origin": "127.0.0.1"}')
```

```
```


