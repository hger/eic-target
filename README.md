systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server

model: host-passthrough

ip address show mgmt-br

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
