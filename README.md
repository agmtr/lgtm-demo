```
# macos

brew install --cask docker
brew install kind kubectl helm helmfile

kind create cluster --config config.yaml
helmfile apply
kubectl apply -f app.yaml

export POD_NAME=$(kubectl get pods --namespace grafana -l "app.kubernetes.io/name=grafana,app.kubernetes.io/instance=grafana" -o jsonpath="{.items[0].metadata.name}")
kubectl --namespace grafana port-forward $POD_NAME 3000

goto http://localhost:3000
