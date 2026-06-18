systemctl stop rke2-server

/opt/rke2/bin/rke2 certificate rotate

systemctl start rke2-server 

model: host-passthrough

kubectl edit kubevirts.kubevirt.io kubevirt -n harvester-system

spec:
  configuration:
    cpuModel: "host-passthrough"

ip address show mgmt-br

instance-label on the badcompany machine, bad: company

virtual machine sceduling all namespaces, Topology Key: kubernetes.io/hostname and Anti-affinity label bad: company

kubectl get events -n kube-system --sort-by='.metadata.creationTimestamp' -w

kubectl describe vm badcompany -n default

kubectl get pods -n kube-system | grep descheduler

kubectl logs -n kube-system <DESCHEDULER_POD_NAME> -f

helm repo add kubernetes-sigs https://kubernetes-sigs.github.io/descheduler/

helm repo update

# values.yaml
cmdOptions:
  v: 2

# Run as a continuous cron/interval instead of a one-time job
deschedulingInterval: "1m"

# Only evict normal VM pods, protect system infrastructure
evictableNamespaces:
  exclude:
    - "kube-system"
    - "cattle-system"
    - "longhorn-system"

deschedulerPolicy:
  strategies:
    # This strategy forces the cluster to fix anti-affinity conflicts
    RemovePodsViolatingInterPodAntiAffinity:
      enabled: true

helm install descheduler kubernetes-sigs/descheduler --namespace kube-system -f values.yaml
