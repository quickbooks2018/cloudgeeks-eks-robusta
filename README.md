# cloudgeeksca

- https://cloudgeeks.ca

### Robusta

- https://home.robusta.dev/

- EKS CSI driver is not install by default
- https://aws.amazon.com/premiumsupport/knowledge-center/eks-troubleshoot-ebs-volume-mounts/

- Verify that the Amazon EBS CSI driver controller and node pods are running
```
kubectl get all -l app.kubernetes.io/name=aws-ebs-csi-driver -n kube-system
```

- https://github.com/kubernetes-sigs/aws-ebs-csi-driver/blob/master/docs/install.md

- CSI Driver Installation
```
chmod +x csidriver.sh
bash -uvx csidriver.sh
```


- export Cluster Name
```
export CLUSTER_NAME='cloudgeeks-eks-dev'
```

- generated_values.yaml

- Robusta Official

- values.yaml

- https://github.com/robusta-dev/robusta/blob/master/helm/robusta/values.yaml


- Install Robusta with Helm

- https://docs.robusta.dev/master/installation.html

```bash
curl -fsSL -o robusta https://docs.robusta.dev/master/_static/robusta

chmod +x robusta

./robusta version

./robusta gen-config

helm repo add robusta https://robusta-charts.storage.googleapis.com && helm repo update

export CLUSTER_NAME='cloudgeeks-eks-dev'

helm upgrade --install \
    robusta robusta/robusta \
    --values generated_values.yaml \
    --namespace monitoring \
    --create-namespace \
    --wait \
    --set clusterName="${CLUSTER_NAME}"
```

- Note: generated_values.yaml is Slack & Robusta UI Account Settings plus BuiltIn Powerful Alerting Rules

- Add Custom Alerting Rules in values.yaml
```
helm upgrade --install \
    robusta robusta/robusta \
    --values generated_values.yaml \
    --namespace monitoring \
    --create-namespace \
    --wait \
    --set clusterName="${CLUSTER_NAME}" \
    --values values.yaml
```
- Robusta Demos
- https://github.com/robusta-dev/kubernetes-demos

- Crashing Pods Demo
```
```crash
kubectl apply -f https://gist.githubusercontent.com/robusta-lab/283609047306dc1f05cf59806ade30b6/raw
```
