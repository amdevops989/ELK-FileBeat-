# ELK-FileBeat-

helm install elasticsearch elastic/elasticsearch -f values-es.yaml -n elk

helm install kibana elastic/kibana -f values-kb.yaml -n elk

kubectl get secret elasticsearch-master-credentials -n elk -o jsonpath='{.data.password}' | base64 --decode; echo