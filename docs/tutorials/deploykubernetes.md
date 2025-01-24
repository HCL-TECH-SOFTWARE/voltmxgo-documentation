# Deploy Kubernetes

--8<-- "devtestenvironment.md"

## Overview

Volt MX Go is deployable with Kubernetes via the following options:

- using [K3s](https://docs.k3s.io) on an Ubuntu, RHEL, SLES machine or VM

- using [Rancher Desktop](https://docs.rancherdesktop.io) running on Windows  

To deploy Kubernetes, **perform only one procedure** from the list:

- Install and configure K3s
- Install Rancher Desktop

!!!warning "Important"
    If you have an existing installation of Volt MX Go and want to upgrade to the latest version, you don't need to deploy Kubernetes as it was already deployed when you first installed Volt MX Go. You can proceed to [Complete preparatory procedure for upgrading an existing installation of Volt MX Go](prereqindex.md#for-upgrading-an-existing-installation-of-volt-mx-go). 

## Install and configure K3s

??? info "Install and configure K3s procedure"
    --8<-- "k3sinstall.md"

## Install Rancher Desktop

??? info "Install Rancher Desktop procedure"
    --8<-- "installrancher.md"