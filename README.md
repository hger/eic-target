systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server 

model: host-passthrough

kubectl port-forward svc/longhorn-frontend -n longhorn-system 8080:80

instance-label on the badcompany machine, bad: company

virtual machine sceduling all namespaces, Topology Key: kubernetes.io/hostname and Anti-affinity label bad: company

kubectl get virtualmachineinstancemigrations -n default -o custom-columns=NAME:.metadata.name,STATUS:.status.phase,AGE:.metadata.creationTimestamp

kubectl describe virtualmachineinstancemigration migration-name -n default | sed -n '/Events:/,$p'

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
