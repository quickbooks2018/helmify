# Kubernetes

- https://spacelift.io/blog/kubernetes-ingress


# Helmify

- Converts k8 yaml files into helm charts

- https://github.com/arttor/helmify

- htps://cloudgeeks.ca

- https://hub.docker.com/r/homebrew/brew


- Helmify installation

- Windows Linux MAC

- Windows
```helmify
docker run --name helmify --network host -w /mnt -v "c:/users/Muhammad Asim/Desktop/helmify:/mnt" -id python:slim

apt update -y && apt install -y curl
curl -# -LO https://github.com/arttor/helmify/releases/download/v0.3.22/helmify_0.3.22_Linux_64-bit.tar.gz
tar -xzvf helmify_0.3.22_Linux_64-bit.tar.gz
mv helmify /usr/local/bin
helmify --version
```

- Linux
```helmify
docker run --name helmify --network host -w /mnt -v "${PWD}/helmify:/mnt" -id python:slim

apt update -y && apt install -y curl
curl -# -LO https://github.com/arttor/helmify/releases/download/v0.4.4/helmify_0.4.4_Linux_64-bit.tar.gz
tar -xzvf helmify_0.4.4_Linux_64-bit.tar.gz
mv helmify /usr/local/bin
helmify --version
```

- MAC
```helmify
docker run --name helmify --network host -w /mnt -v "${PWD}/helmify:/mnt" -id python:slim

apt update -y && apt install -y curl
curl -# -LO https://github.com/arttor/helmify/releases/download/v0.3.22/helmify_0.3.22_Linux_64-bit.tar.gz
tar -xzvf helmify_0.3.22_Linux_64-bit.tar.gz
mv helmify /usr/local/bin
helmify --version
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

##### Helm --dry-run & --debug both contact cluster but when you add template eg. Helm template --debug --dry-run it will not contact cluster
```helm
helm template -f cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace cloudgeeks-helm-chart/ --debug

helm template -f cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace cloudgeeks-helm-chart/ --debug --dry-run

helm install cloudgeeks ./cloudgeeks-helm-chart/ -f ./cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace --debug --dry-run

helm install cloudgeeks ./cloudgeeks-helm-chart/ -f ./cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace

helm upgrade --install cloudgeeks ./cloudgeeks-helm-chart/ -f ./cloudgeeks-helm-chart/values.yaml --namespace cloudgeeks --create-namespace

```
