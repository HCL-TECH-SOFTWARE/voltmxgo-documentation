# Installation

This tutorial will guide you through the procedures for installing the Early Access version of Volt MX Go.

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
2. [Prerequisite procedures](prereq.md)
3. [Download Domino/Keep Helm chart](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)
6. [Connect to Domino server from Notes client](connectdominofromnotes.md)

**When using Rancher Desktop running on Windows:**

1. [Install Rancher Desktop](installrancher.md)
2. [Prerequisite procedures](prereq.md)
3. [Download Domino/Keep Helm chart](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)
6. [Connect to Domino server from Notes client](connectdominofromnotes.md)