systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server

model: host-passthrough

vi /etc/rancher/rke2/config.yaml.d/50-rancher.yaml

"node-monitor-grace-period=15s",

"pod-eviction-timeout=15s"

kubectl get pods -n default | grep noonelikesyou

kubectl delete pod <STUCK-POD-NAME> -n default --force --grace-period=0

spec:
  template:
    spec:
      tolerations:
      - key: "node.kubernetes.io/unreachable"
        operator: "Exists"
        effect: "NoExecute"
        tolerationSeconds: 10
      - key: "node.kubernetes.io/not-ready"
        operator: "Exists"
        effect: "NoExecute"
        tolerationSeconds: 10
