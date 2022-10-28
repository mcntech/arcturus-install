# arcturus-install
Arcturus Edge Security

## Test
Run the cluster
```
docker-compose --profile test up -d
```

check pipeline
```
curl -X POST -H "Content-Type: application/json" --data '{"message": "Hello"}' localhost:8000/routem/api/echo
curl -X POST -H "Content-Type: application/json" --data '{"message": "Hello"}' localhost:8000/routen/api/echo
```
