# arcturus-install
Arcturus Edge Security

## Test

kong.yml
```
_format_version: '2.1'
services:
- name: test-service1
  url: http://192.168.0.160:9430
  routes:
  - name: test-route1
    paths:
    - '/service1'
  plugins:
  - name: arcturus_plugin
- name: test-service2
  url: http://192.168.0.160:9428
  routes:
  - name: test-route2
    paths:
    - '/service2'
  plugins:
  - name: arcturus_plugin

```
Run the cluster
```
docker-compose --profile test up -d
```

check pipeline without authorization header
```
curl -X POST -H "Content-Type: application/json" --data '{"message": "Hello"}' localhost:8000/service1/api/echo
curl -X POST -H "Content-Type: application/json" --data '{"message": "Hello"}' localhost:8000/service2/api/echo
```

check pipeline with authorization header
Local testing
GET Method

curl -i -X GET --header "Authorization: Bearer 0x7b224e616d65223a224172637475727573222c22546f6b656e223a2231222c22436f6e7472616374223a22307830303030303044623832343939613630386245374533374637383130343734324566364431303243222c22436861696e223a22313337227d.0x7ec978d2cf87123f1112332772663bbb309ff9e2ba229b2cb8dd04444edc862d30145563d70e9e2e2d580efa99bfd6a73d1cb376cc176fb070b5add8ca5bc02901" http://localhost:8000/service1

Post Method
```
curl -i -X curl -X POST --header "Authorization: Bearer 0x7b224e616d65223a224172637475727573222c22546f6b656e223a2231222c22436f6e7472616374223a22307830303030303044623832343939613630386245374533374637383130343734324566364431303243222c22436861696e223a22313337227d.0x7ec978d2cf87123f1112332772663bbb309ff9e2ba229b2cb8dd04444edc862d30145563d70e9e2e2d580efa99bfd6a73d1cb376cc176fb070b5add8ca5bc02901" -H "Content-Type: application/json" --data '{"message": "Hello"}'  http://localhost:8000/service1/api/echo
```

