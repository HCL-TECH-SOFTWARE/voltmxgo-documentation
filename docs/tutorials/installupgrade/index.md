# Install and upgrade

Guides you through the procedures for installing and upgrading Volt MX Go.

!!! warning "Important"

    The installation and upgrade processes for Volt Foundry and Volt Iris differ based on Volt MX Go release version. 
    
    **For Volt MX Go v10**:

    - Volt Foundry is first installed. A Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work.
    - The installed Volt Iris  must be connected to a supported version of Volt Foundry that has been activated with a Volt MX Go license in My HCLSoftware Portal for the Volt MX Go capabilities to be visible in Volt Iris. 

    **For Volt MX Go v2.1 up to v2.1.2**:

    - Volt Foundry and Volt Iris are first installed, followed by installing the necessary plugins using the Volt MX Go Plugin Installer. The plugins enable the capabilities unique to Volt MX Go. 
    - Volt Foundry must be licensed with a Volt MX Go entitlement for the plugins to be enabled and for the Volt MX Go features to work.
    - After installing the plugins, connect Volt Iris to Volt Foundry licensed with a Volt MX Go entitlement to enable and use the Volt MX Go features in Volt Iris.

<!--## Before you begin

In case you would like to deploy Volt MX Go in a **development or test only environment**, you can do so with Kubernetes using the following options:

- using [K3s](https://docs.k3s.io) on an Ubuntu, RHEL, SLES machine or VM

- using [Rancher Desktop](https://docs.rancherdesktop.io) running on Windows
-->

## System requirements

Before starting the installation, make sure to verify that you meet the [System requirements](sysreq/index.md).

## Install and upgrade guide

To install the server components of Volt MX Go, proceed to [Install Volt MX Go server components](installserver/index.md).

To upgrade the server components of Volt MX Go, proceed to [Upgrade Volt MX Go server components](upgradeserver/index.md).

To install and upgrade Volt Iris, proceed to [Install and upgrade Volt Iris](installiris/index.md).
