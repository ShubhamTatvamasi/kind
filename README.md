# kind

start kind cluster:
```bash
kind create cluster
```

load image on kind cluster:
```bash
kind load docker-image magmacore/nginx:1.4.0
```

check all the images available on kind cluster:
```bash
docker exec -it kind-control-plane crictl images
```

delete cluster:
```bash
kind delete cluster
```

### LoadBalancer

Install [metallb](https://metallb.universe.tf/installation/#installation-by-manifest)

check the IP range for kind docker network:
```bash
docker network inspect -f '{{.IPAM.Config}}' kind
```

Setup address pool:
```
kubectl create -f - << EOF
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: metallb-system
  name: config
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - 172.18.255.200-172.18.255.250
EOF
```


