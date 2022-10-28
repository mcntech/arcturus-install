# arcturus-install
Arcturus Edge Security

## Test
Run the cluster
```
docker-compose up -d
```

check pipeline
```
curl -X POST -H "Content-Type: application/json" --data '{"message": "Hello"}' localhost:8000/api/echo
```
