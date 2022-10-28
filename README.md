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
```
curl -i -X curl -X POST --header "Authorization: Bearer 0x68656c6c6f.0xca4e7e1113e87703aa8d8745ad478da13afe2210b3ff098a685521b7912dc2b6251abc3ed475cd4be2e31da958c7feb8b79bbd452608436b2ed92d52775b36ad01" -H "Content-Type: application/json" --data '{"message": "Hello"}'  http://localhost:8000/service1/api/echo
```

