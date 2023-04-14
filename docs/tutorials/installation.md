# Installation

Guides you through the procedures for installing the Early Access version of Volt MX Go.

## Before you start

The Early Access version of Volt MX Go is deployed with Kubernetes via the following options:

- using [K3s](https://docs.k3s.io) on an Ubuntu, RHEL, SLES machine or VM
- using [Rancher Desktop](https://docs.rancherdesktop.io) running on Windows  


## System requirements
Before starting the installation, make sure to verify that you meet the [System requirements](../references/sysreq.md).

## Installation guide

Follow the order for completing the procedures according to your preferred deployment option.

**When using K3s on an Ubuntu, RHEL, SLES machine or VM:**

1. [Install and configure K3s](k3sinstall.md)
2. [Complete prerequisite procedures](prereq.md)
3. [Download Domino/Keep Helm chart](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)
6. [Connect to Domino server from Notes client](connectdominofromnotes.md)

**When using Rancher Desktop running on Windows:**

1. [Install Rancher Desktop](installrancher.md)
2. [Complete prerequisite procedures](prereq.md)
3. [Download Domino/Keep Helm chart](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)
6. [Connect to Domino server from Notes client](connectdominofromnotes.md)

!!!tip
    You can see [FAQ and common procedures](../references/kubecheatsheet.md) for additional information.

## Installing Volt MX Go Iris

1.  Download Volt Iris from [HCL Software License & Download Portal](https://id.hcltechsw.com/).

    !!!tip
        For more information on how to download from the portal, see [Download from HCL License & Download Portal](../howto/portaldownload.md).

2.  Install Volt MX Iris.
    - [For Mac](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_mac/Content/Installing%20VoltMX%20Iris.html#installing)
    - [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_win/Content/Installing%20VoltMX%20Iris.html#installing)
3. Login to your Volt Foundry Server.
4. Add the `com.hcl.rosetta.sdk_<version>.jar` to your `.plugins` directory in the Iris workspace directory.
    
    !!!note
        Create the `.plugins` directory as needed.