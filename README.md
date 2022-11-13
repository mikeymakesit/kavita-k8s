# Kavita Comic Server on Kubernetes

Deploy Kavita to Kubernetes using a Kustomize overlay.

You will need to edit `kustomize/overlays/local/kustomization.yaml` to
specify the following for your environment:

1. Hostname for your ingress
1. Amount of space to reserve in a PersistentVolumeClaim for Kavita to use
1. The location of a volume where your library is located

## K8s or K3s

```bash
kubectl apply kustomize/overlays/local
```

## App config

The Kavita config and all the covers are stored in the PersistentVolumeClaim.
If you delete that or your entire namespace, you'll lose that and have to 
recreate it.

## Test in Podman

Run a test container using Podman instead:

```bash
podman run -d --name kavita \
    -v /path/to/kavita/config:/kavita/config \
    -v /path/to/Comics:/comics \
    -v /path/to/Magazines:/magazines \
    -p 5000:5000 \
    --restart unless-stopped \
    --pull always \
    docker.io/kizaing/kavita:latest
```

## Reference

[Kavita official repo](https://github.com/Kareadita/Kavita)

