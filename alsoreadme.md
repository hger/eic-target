harvester-01:~ # kubectl describe vmi slesvm-longhorn
Name:         slesvm-longhorn
Namespace:    default
Labels:       harvesterhci.io/vmName=slesvm-longhorn
              kubevirt.io/migrationTargetNodeName=harvester-03
              kubevirt.io/nodeName=harvester-03
Annotations:  harvesterhci.io/sshNames: []
              kubevirt.io/latest-observed-api-version: v1
              kubevirt.io/nonroot: true
              kubevirt.io/storage-observed-api-version: v1
              kubevirt.io/vm-generation: 16
API Version:  kubevirt.io/v1
Kind:         VirtualMachineInstance
Metadata:
  Creation Timestamp:  2026-06-17T10:57:31Z
  Finalizers:
    kubevirt.io/virtualMachineControllerFinalize
    foregroundDeleteVirtualMachine
    wrangler.cattle.io/harvester-lb-vmi-controller
  Generation:  54
  Owner References:
    API Version:           kubevirt.io/v1
    Block Owner Deletion:  true
    Controller:            true
    Kind:                  VirtualMachine
    Name:                  slesvm-longhorn
    UID:                   d7a2d0cc-6dd3-41de-bff7-fcea88db58fe
  Resource Version:        42004092
  UID:                     28082667-8121-4e64-9c3b-bbd19869356c
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
  Eviction Strategy:  LiveMigrateIfPossible
  Hostname:           slesvm-longhorn
  Networks:
    Name:  default
    Pod:
  Termination Grace Period Seconds:  120
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
    505b6771-dac9-48f4-9121-27725cf6db73:  harvester-01
    6275a76a-b841-4b4f-9dc1-ae1c391bc2bc:  harvester-03
    e6a0abc6-618f-4ade-a01c-d917bdc99c8c:  harvester-01
  Conditions:
    Last Probe Time:       2026-06-17T12:51:06Z
    Last Transition Time:  2026-06-17T12:51:06Z
    Message:               virt-launcher pod is terminating
    Reason:                PodTerminating
    Status:                False
    Type:                  Ready
    Last Probe Time:       <nil>
    Last Transition Time:  <nil>
    Status:                True
    Type:                  LiveMigratable
    Last Probe Time:       <nil>
    Last Transition Time:  <nil>
    Status:                True
    Type:                  StorageLiveMigratable
    Last Probe Time:       2026-06-17T10:58:09Z
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
    Ip Address:      10.52.2.57
    Ip Addresses:
      10.52.2.57
    Mac:                             ca:1d:63:b2:80:ea
    Name:                            default
    Queue Count:                     1
  Launcher Container Image Version:  registry.suse.com/suse/sles/15.6/virt-launcher:1.4.0-150600.5.15.1
  Machine:
    Type:  pc-q35-8.2
  Memory:
    Guest At Boot:    4Gi
    Guest Current:    4Gi
    Guest Requested:  4Gi
  Migration Method:   BlockMigration
  Migration State:
    Completed:      true
    End Timestamp:  2026-06-17T12:42:52Z
    Migration Configuration:
      Allow Auto Converge:                    false
      Allow Post Copy:                        false
      Bandwidth Per Migration:                0
      Completion Timeout Per Gi B:            150
      Node Drain Taint Key:                   kubevirt.io/drain
      Parallel Migrations Per Cluster:        5
      Parallel Outbound Migrations Per Node:  2
      Progress Timeout:                       150
      Unsafe Migration Override:              false
    Migration UID:                            411080b7-79ce-4e62-b84d-8eb59b8dab86
    Mode:                                     PreCopy
    Source Node:                              harvester-01
    Source Pod:                               virt-launcher-slesvm-longhorn-mc5c6
    Start Timestamp:                          2026-06-17T12:42:49Z
    Target Direct Migration Node Ports:
      42329:                             49153
      44797:                             0
      46469:                             49152
    Target Node:                         harvester-03
    Target Node Address:                 10.52.2.56
    Target Node Domain Detected:         true
    Target Node Domain Ready Timestamp:  2026-06-17T12:42:52Z
    Target Pod:                          virt-launcher-slesvm-longhorn-2k7dw
  Migration Transport:                   Unix
  Node Name:                             harvester-03
  Phase:                                 Running
  Phase Transition Timestamps:
    Phase:                        Pending
    Phase Transition Timestamp:   2026-06-17T10:57:31Z
    Phase:                        Scheduling
    Phase Transition Timestamp:   2026-06-17T10:57:31Z
    Phase:                        Scheduled
    Phase Transition Timestamp:   2026-06-17T10:57:44Z
    Phase:                        Running
    Phase Transition Timestamp:   2026-06-17T10:57:45Z
  Qos Class:                      Burstable
  Runtime User:                   107
  Selinux Context:                none
  Virtual Machine Revision Name:  revision-start-vm-d7a2d0cc-6dd3-41de-bff7-fcea88db58fe-16
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
  Type    Reason            Age                From                         Message
  ----    ------            ----               ----                         -------
  Normal  SuccessfulUpdate  13m                virtualmachine-controller    Expanded PodDisruptionBudget kubevirt-disruption-budget-dk2k4
  Normal  Migrating         12m (x2 over 79m)  virt-handler                 VirtualMachineInstance is migrating.
  Normal  PreparingTarget   12m (x2 over 12m)  virt-handler                 VirtualMachineInstance Migration Target Prepared.
  Normal  PreparingTarget   12m                virt-handler                 Migration Target is listening at 10.52.2.56, on ports: 44797,46469,42329
  Normal  Migrated          12m (x2 over 79m)  virt-handler                 The VirtualMachineInstance migrated to node harvester-03.
  Normal  Deleted           12m (x2 over 79m)  virt-handler                 Signaled Deletion
  Normal  SuccessfulUpdate  12m                disruptionbudget-controller  shrank PodDisruptionBudget kubevirt-disruption-budget-dk2k4

