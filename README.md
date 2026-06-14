systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server

model: host-passthrough

kubectl set env deployment/kube-controller-manager -n kube-system NODE_MONITOR_GRACE_PERIOD=15s

kubectl set env deployment/kube-controller-manager -n kube-system POD_EVICTION_TIMEOUT=15s

vi /etc/rancher/rke2/config.yaml.d/50-rancher.yaml

"node-monitor-grace-period=15s",

"pod-eviction-timeout=15s"

kubectl get pods -n default | grep noonelikesyou

kubectl delete pod <STUCK-POD-NAME> -n default --force --grace-period=0
