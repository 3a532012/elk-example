先建立ECK環境

kubectl create -f https://download.elastic.co/downloads/eck/2.10.0/crds.yaml
kubectl apply -f https://download.elastic.co/downloads/eck/2.10.0/operator.yaml
kubectl -n elastic-system logs -f statefulset.apps/elastic-operator


所有的資源都在namespace: kube-system下
除了產生log的pod test.yaml