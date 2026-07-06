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

kubectl -n harvester-system get upgrades.harvesterhci.io -l harvesterhci.io/latestUpgrade=true -o yaml
