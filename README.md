# rancher-cluster-templates

Rancher Cluster Templates to provision RKE2 Kubernetes clusters on VMware cloud provider.  
Template files ready to import to repository related to chart repository connected to Rancher environment.

## How to Use

* Template files should be embedded in a properly configured repository connected to the Rancher ecosystem at the Rancher Management Server level
* Used (connected to RMS) repository should be properly structured according to the requirements of the charts repository

Great examples (also inspired by :)) in repositories:  
https://github.com/rancher/cluster-template-examples  
https://github.com/bashofmann/rancher-cluster-templates

## Prerequisities:
* existing on RMS cloud credential to VMware vSphere environment with appropriate permission
* existing on VMware and configured as required VM template to provision cluster nodes
