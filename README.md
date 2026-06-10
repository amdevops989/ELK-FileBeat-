# ELK-FileBeat-

helm install elasticsearch elastic/elasticsearch -f values-es.yaml -n elk

helm install kibana elastic/kibana -f values-kb.yaml -n elk

kubectl get secret elasticsearch-master-credentials -n elk -o jsonpath='{.data.password}' | base64 --decode; echo

use the username elastic


helm install logstash elastic/logstash -f values-ls.yaml -n elk

curl -XPOST 'http://localhost:9600' \
-H 'Content-Type: application/json' \
-d '{"message": "Hello ELK Stack! Testing my Logstash pipeline.", "environment": "minikube", "status": "operational"}'

 helm install filebeat elastic/filebeat -f values-fb.yaml -n elk
