# Kubernetes

- https://spacelift.io/blog/kubernetes-ingress


# Helmify

- Converts k8 yaml files into helm charts

- https://github.com/arttor/helmify

- htps://cloudgeeks.ca

- https://hub.docker.com/r/homebrew/brew


- Helmify installation

- Windows Linux MAC

```helmify
docker run --name helmify --network host -w /mnt -v "c:/users/Muhammad Asim/Desktop/helmify:/mnt" -id homebrew/brew:latest

docker exec -it helmify bash

brew install arttor/tap/helmify
```

- Helmify commands From Directory
```helmify
export DIR='k8'
awk 'FNR==1 && NR!=1  {print "---"}{print}' ${DIR}/*.yaml | helmify -vv cloudgeeks-helm-chart 
```

- Helmify commands From file
```helmify
cat my-app.yaml | helmify -vv cloudgeeks-helmchart
```

# Kompose

- Convert docker-compose in to kubernetes yaml files

- https://kubernetes.io/docs/tasks/configure-pod-container/translate-compose-kubernetes/

- https://github.com/kubernetes/kompose

- https://github.com/kubernetes/kompose/blob/master/docs/installation.md#docker

- https://github.com/kubernetes/kompose/releases

- Examples https://github.com/kubernetes/kompose/tree/master/examples

```kompose
docker exec -u root -it helmify bash
apt update -y && apt install -y sudo
curl -L https://github.com/kubernetes/kompose/releases/download/v1.27.0/kompose-linux-amd64 -o kompose
chmod +x kompose
sudo mv ./kompose /usr/local/bin/kompose
kompose convert --help
kompose convert --with-kompose-annotation=false -f docker-compose.yaml
```

##### Helm
```helm
helm template -f cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace cloudgeeks-helm-chart/ --debug --dry-run

helm install cloudgeeks ./cloudgeeks-helm-chart/ -f ./cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace --debug--dry-run

helm install cloudgeeks ./cloudgeeks-helm-chart/ -f ./cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace

helm upgrade --install cloudgeeks ./cloudgeeks-helm-chart/ -f ./cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace

```
