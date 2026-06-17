systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server 

model: host-passthrough
evictionStrategy: None
terminationGracePeriodSeconds: 10

kubectl patch setting.longhorn.io node-down-pod-deletion-policy -n longhorn-system --type merge -p '{"value":"delete-both-statefulset-and-deployment-pod"}'

kubectl get setting.longhorn.io node-down-pod-deletion-policy -n longhorn-system

instance-label on the badcompany machine, bad: company

virtual machine sceduling all namespaces, Topology Key: kubernetes.io/hostname and Anti-affinity label bad: company

kubectl get pod -n default -l kubevirt.io/vm=slesvm-longhorn -o jsonpath='{.items[*].metadata.finalizers}'

try these if and when same issue again

kubectl get volumeattachments

kubectl describe volumeattachment <ATTACHMENT_NAME>

kubectl get events -n kube-system --field-selector reason=VolumeResizeFailed -w
# Or look globally for attachment blocks:
kubectl get events --all-namespaces --field-selector reason=FailedAttachVolume

kubectl get vmi slesvm-longhorn -o jsonpath='{.status.conditions}' | jq

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
