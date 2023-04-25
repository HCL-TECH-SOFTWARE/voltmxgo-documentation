# Installation

Guides you through the procedures for installing the Early Access version of Volt MX Go.

## Before you start

The server components of the Early Access version of Volt MX Go are deployed with Kubernetes via the following options:

- using [K3s](https://docs.k3s.io) on an Ubuntu, RHEL, SLES machine or VM
- using [Rancher Desktop](https://docs.rancherdesktop.io) running on Windows  

!!!note
    HCL Project KEEP has been re-branded to [HCL Domino REST API](../references/index.md#hcl-domino-rest-api-formerly-known-as-hcl-project-keep) to align with the HCL Volt MX Go strategy. However, you might still find references to the KEEP branding throughout the product and in the documentation.
## System requirements
Before starting the installation, make sure to verify that you meet the [System requirements](sysreq.md).

## Installation guide

!!!note
    Make sure that you have completed all the [prerequisite procedures](prerequisite.md) before proceeding with the following procedures. 

Follow the order for completing the procedures according to your preferred deployment option.

**When using K3s on an Ubuntu, RHEL, SLES machine or VM:**

1. [Install and configure K3s](k3sinstall.md)
2. [Complete preparatory procedures](prereq.md)
3. [Install Domino/Keep](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)


**When using Rancher Desktop running on Windows:**

1. [Install Rancher Desktop](installrancher.md)
2. [Complete preparatory procedures](prereq.md)
3. [Install Domino/Keep](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)

!!!tip
    See [FAQ and common procedures](../references/kubecheatsheet.md) for more information about Kubernetes commands.

After completing the procedures based on your preferred deployment option, proceed to [Install Volt MX Go Iris](installiris.md).