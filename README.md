systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate --server

systemctl start rke2-server

model: host-passthrough

kubectl set env deployment/kube-controller-manager -n kube-system NODE_MONITOR_GRACE_PERIOD=15s

kubectl set env deployment/kube-controller-manager -n kube-system POD_EVICTION_TIMEOUT=15s
