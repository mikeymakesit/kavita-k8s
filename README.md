# Kavita Comic Server

Something to compare with Ubooquity.

## K8s

```bash
kubectl apply kustomize/base
```

## Docker

Run test container:

```bash
podman run -d --name kavita \
    -v /home/mike/projects/kavita/config:/kavita/config \
    -v /home/mike/Desktop/nas/Comics:/comics \
    -v /home/mike/Desktop/nas/Magazines:/magazines \
    -p 5000:5000 \
    --restart unless-stopped \
    docker.io/kizaing/kavita:latest
```

Project repo:

<https://github.com/Kareadita/Kavita>
