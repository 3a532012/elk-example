先建立ECK環境

kubectl create -f https://download.elastic.co/downloads/eck/2.10.0/crds.yaml
kubectl apply -f https://download.elastic.co/downloads/eck/2.10.0/operator.yaml
kubectl -n elastic-system logs -f statefulset.apps/elastic-operator


所有的資源都在namespace: kube-system下
除了產生log的pod test.yaml

取得elasticsearch密碼
PASSWORD=$(kubectl get secret quickstart-es-elastic-user -o go-template='{{.data.elastic | base64decode}}' -n kube-system) | echo $PASSWORD

並且將密碼修改到 filebeat的ELASTICSEARCH_PASSWORD上


kubectl port-forward service/quickstart-kb-http 5601 -n kube-system

將流量導到https://localhsot:5601