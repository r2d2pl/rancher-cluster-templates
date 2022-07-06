# rancher-cluster-templates

Rancher Cluster Templates to provision RKE2 Kubernetes clusters on VMware cloud provider.  
Template files ready to import to repository related to chart repository connected to Rancher Management Server (RMS) environment.

## Prerequisities:
:point_right: existing on RMS cloud credential to VMware vSphere environment with appropriate permission  
:point_right: existing on VMware and configured as required VM template to provision cluster nodes  
:point_right: in this example we assume provisioning of nodes based on transport with the use of VMTools mechanisms (vappTransport: com.vmware.guestInfo) and VMware vApp properties (properties used in the script configuration at the cloud-init layer level)  

## How to Use
:arrow_forward: In order to customize the templates, it is necessary to modify some parameters in the following lines (places) according to the properties of the target environment ('NAME'):  

:twisted_rightwards_arrows: In file: **values.yaml** (cloud credential is hardcoded so it is necessary to rename a secret name to appropriate to appropriate for the target RMS environment)
```
cloudCredentialSecretName: "cattle-global-data:xx-abcde"
```
:twisted_rightwards_arrows: In files: **nodeconfig-controlplane.yaml**, **nodeconfig-worker.yaml**
```
cloneFrom: /DCNAME/vm/ClusterNAME/Templates/ubuntu-focal-cloudimg-templateNAME
cloudConfig: ... search: [your.domainNAME,your.nextdomainNAME]\n
datacenter: /DCNAME
datastore: /DCNAME/datastore/datastoreNAME
folder: /DCNAME/vm/ClusterNAME/VMFolderNAME
hostsystem: /DCNAME/host/ClusterNAME/esxi.host.fqdnNAME
network:
- /DCNAME/network/VMNetworkNAME
pool: /DCNAME/host/ClusterSahul/Resources
vappProperty:
- guestinfo.interface.0.ip.0.address=ip:VMNetworkNAME
- guestinfo.interface.0.ip.0.netmask=${netmask:VMNetworkNAME}
- guestinfo.interface.0.route.0.gateway=${gateway:VMNetworkNAME}
- guestinfo.dns.servers=${dns:VMNetworkNAME}
```
:arrow_forward: Template files should be embedded in a repository connected to the Rancher ecosystem at the Rancher Management Server level  
:arrow_forward: Used (connected to RMS) repository should be properly structured according to the requirements of the charts repository

Great examples (also as a source of inspiration :heart_eyes:) in repositories:  
https://github.com/rancher/cluster-template-examples  
https://github.com/bashofmann/rancher-cluster-templates
