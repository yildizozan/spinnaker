Install kubectl
```bash
apt-get update && apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update
apt-get install -y kubectl
apt-mark hold kubectl
```

Well, now create kube folder for kubeconfig file then copy config file to kube folder. Kubeconfig file provide to connect cluster.
```bash
mkdir ~/.kube
cp $CONFIG_FILE_PATH ~/.kube
```
We can access spinnaker!
```bash
kubectl -n spinnaker port-forward service/spin-deck 9000 &
kubectl -n spinnaker port-forward service/spin-gate 8084 &
```

Congrats!
