# kind

start kind cluster:
```bash
kind create cluster
```

load image on kind cluster:
```bash
kind load docker-image magmacore/nginx:1.4.0
```

get inside kind container:
```bash
docker exec -it kind-control-plane bash
```

check all the images available on kind cluster:
```bash
crictl images
```
