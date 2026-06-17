harvester-02:~ # kubectl describe vmi slesvm-longhorn
Name:         slesvm-longhorn
Namespace:    default
Labels:       harvesterhci.io/vmName=slesvm-longhorn
              kubevirt.io/nodeName=harvester-02
Annotations:  harvesterhci.io/sshNames: []
              kubevirt.io/latest-observed-api-version: v1
              kubevirt.io/storage-observed-api-version: v1
              kubevirt.io/vm-generation: 22
API Version:  kubevirt.io/v1
Kind:         VirtualMachineInstance
Metadata:
  Creation Timestamp:  2026-06-17T13:39:06Z
  Finalizers:
    kubevirt.io/virtualMachineControllerFinalize
    foregroundDeleteVirtualMachine
    wrangler.cattle.io/harvester-lb-vmi-controller
  Generation:  12
  Owner References:
    API Version:           kubevirt.io/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  VirtualMachine
    Name:                  slesvm-longhorn
    UID:                   d7a2d0cc-6dd3-41de-bff7-fcea88db58fe
  Resource Version:        42048437
  UID:                     3cfa3af6-c6ed-4db6-a4c2-1e5374683f84
Spec:
  Affinity:
    Pod Affinity:
    Pod Anti Affinity:
      Required During Scheduling Ignored During Execution:
        Label Selector:
          Match Expressions:
            Key:       bad
            Operator:  In
            Values:
              company
        Namespace Selector:
        Topology Key:  kubernetes.io/hostname
  Architecture:        amd64
  Domain:
    Cpu:
      Cores:    2
      Model:    host-passthrough
      Sockets:  1
      Threads:  1
    Devices:
      Disks:
        Boot Order:  1
        Disk:
          Bus:  virtio
        Name:   disk-0
        Disk:
          Bus:  virtio
        Name:   cloudinitdisk
      Inputs:
        Bus:   usb
        Name:  tablet
        Type:  tablet
      Interfaces:
        Mac Address:  ca:1d:63:b2:80:ea
        Masquerade:
        Model:  virtio
        Name:   default
    Features:
      Acpi:
        Enabled:  true
    Firmware:
      Uuid:  4699c439-9fa8-5278-a6a8-88df35ca65cd
    Machine:
      Type:  q35
    Memory:
      Guest:  4Gi
    Resources:
      Limits:
        Cpu:     2
        Memory:  4Gi
      Requests:
        Cpu:          125m
        Memory:       2730Mi
  Eviction Strategy:  None
  Hostname:           slesvm-longhorn
  Networks:
    Name:  default
    Pod:
  Termination Grace Period Seconds:  10
  Tolerations:
    Effect:              NoExecute
    Key:                 node.kubernetes.io/unreachable
    Operator:            Exists
    Toleration Seconds:  10
    Effect:              NoExecute
    Key:                 node.kubernetes.io/not-ready
    Operator:            Exists
    Toleration Seconds:  10
  Volumes:
    Name:  disk-0
    Persistent Volume Claim:
      Claim Name:  slesvm-longhorn-disk-0-xa58w
    Cloud Init No Cloud:
      Network Data Secret Ref:
        Name:  slesvm-longhorn-zgw6j
      Secret Ref:
        Name:  slesvm-longhorn-zgw6j
    Name:      cloudinitdisk
Status:
  Active Pods:
    fc5c0222-faaf-4e23-8f7c-33204d7fda84:  harvester-02
  Conditions:
    Last Probe Time:       <nil>
    Last Transition Time:  2026-06-17T13:39:18Z
    Status:                True
    Type:                  Ready
    Last Probe Time:       <nil>
    Last Transition Time:  <nil>
    Status:                True
    Type:                  LiveMigratable
    Last Probe Time:       <nil>
    Last Transition Time:  <nil>
    Status:                True
    Type:                  StorageLiveMigratable
    Last Probe Time:       2026-06-17T13:39:38Z
    Last Transition Time:  <nil>
    Status:                True
    Type:                  AgentConnected
  Current CPU Topology:
    Cores:    2
    Sockets:  1
    Threads:  1
  Guest OS Info:
    Id:              sles
    Kernel Release:  6.4.0-150600.23.38-default
    Kernel Version:  #1 SMP PREEMPT_DYNAMIC Thu Feb  6 08:53:28 UTC 2025 (cb92f8c)
    Machine:         x86_64
    Name:            SLES
    Pretty Name:     SUSE Linux Enterprise Server 15 SP6
    Version:         15-SP6
    Version Id:      15.6
  Interfaces:
    Info Source:     domain, guest-agent
    Interface Name:  eth0
    Ip Address:      10.52.1.157
    Ip Addresses:
      10.52.1.157
    Mac:                             ca:1d:63:b2:80:ea
    Name:                            default
    Queue Count:                     1
  Launcher Container Image Version:  registry.suse.com/suse/sles/15.6/virt-launcher:1.4.0-150600.5.15.1
  Machine:
    Type:  pc-q35-8.2
  Memory:
    Guest At Boot:      4Gi
    Guest Current:      4Gi
    Guest Requested:    4Gi
  Migration Method:     BlockMigration
  Migration Transport:  Unix
  Node Name:            harvester-02
  Phase:                Running
  Phase Transition Timestamps:
    Phase:                        Pending
    Phase Transition Timestamp:   2026-06-17T13:39:06Z
    Phase:                        Scheduling
    Phase Transition Timestamp:   2026-06-17T13:39:06Z
    Phase:                        Scheduled
    Phase Transition Timestamp:   2026-06-17T13:39:18Z
    Phase:                        Running
    Phase Transition Timestamp:   2026-06-17T13:39:20Z
  Qos Class:                      Burstable
  Runtime User:                   107
  Selinux Context:                none
  Virtual Machine Revision Name:  revision-start-vm-d7a2d0cc-6dd3-41de-bff7-fcea88db58fe-22
  Volume Status:
    Name:    cloudinitdisk
    Size:    1048576
    Target:  vdb
    Name:    disk-0
    Persistent Volume Claim Info:
      Access Modes:
        ReadWriteMany
      Capacity:
        Storage:            10Gi
      Claim Name:           slesvm-longhorn-disk-0-xa58w
      Filesystem Overhead:  0
      Requests:
        Storage:    10Gi
      Volume Mode:  Block
    Target:         vda
Events:
  Type    Reason            Age    From                       Message
  ----    ------            ----   ----                       -------
  Normal  SuccessfulCreate  5m10s  virtualmachine-controller  Created virtual machine pod virt-launcher-slesvm-longhorn-mtn7q
  Normal  Created           4m56s  virt-handler               VirtualMachineInstance defined.
  Normal  Started           4m56s  virt-handler               VirtualMachineInstance started.
