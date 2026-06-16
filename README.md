systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server

model: host-passthrough

ip address show mgmt-br

https://releases.rancher.com/harvester/v1.6.1/version.yaml

kubectl annotate upgrade.harvesterhci.io -n harvester-system hvst-upgrade-gvw6f upgrade.harvesterhci.io/reconcile-at=$(date +%s) --overwrite

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
