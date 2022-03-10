# Magma

Get list of magma docker images from kind cluster:
```bash
docker exec -it orc8r-control-plane crictl images | tail -n +2 > /tmp/magma_docker_images.tmp

while read line;
do
echo "$(echo ${line} | awk '{print $1}'):$(echo ${line} | awk '{print $2}')"
done < /tmp/magma_docker_images.tmp
```
