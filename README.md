systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server

model: host-passthrough

kubectl get configmap -n harvester-system kubevirt-io-vmi-management-lock -o jsonpath='{ .data.cp }'

vi /etc/rancher/rke2/config.yaml.d/50-rancher.yaml

"node-monitor-grace-period=15s",

"pod-eviction-timeout=15s"

kubectl get pods -n default | grep noonelikesyou

kubectl delete pod <STUCK-POD-NAME> -n default --force --grace-period=0
