systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server

model: host-passthrough

ip address show mgmt-br

https://releases.rancher.com/harvester/v1.6.1/version.yaml

UPGRADE_NAME=$(kubectl -n harvester-system get upgrades -l harvesterhci.io/latestUpgrade=true -o jsonpath='{.items[0].metadata.name}')

kubectl annotate upgrade -n harvester-system $UPGRADE_NAME upgrade.harvesterhci.io/reconcile-at=$(date +%s) --overwrite

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
