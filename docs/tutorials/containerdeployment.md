# Install and upgrade Volt MX Go v2.0.4 or earlier to development or test environment

Perform a new or an upgrade installation of Volt MX Go server components to a development or test only environment to allow you to try its different features in a safe environment. **This isn't intended for a production environment**.

!!!note
    Before starting the installation, make sure to verify that you meet the [System requirements](sysreq.md).

<!--
## For Volt MX Go v2.1

The server components of Volt MX Go can be deployed with Kubernetes or Docker.

### For installing Volt MX Go

Follow the order for completing the procedures according to your preferred deployment option. 

**When using Docker**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).
2. [Run Domino REST API with a Docker image](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/docker.html)
3. [Install Volt MX Go Foundry using Volt Foundry Single Container Solution](nativeinstallers.md#for-single-container-solution)


**When using Kubernetes**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).
2. Run Domino REST API (procedure to be created)
3. [Install Volt MX Go Foundry using helm charts](nativeinstallers.md#for-using-helm-charts-on-a-supported-kubernetes-platform)
-->

The server components of Volt MX Go can be deployed with Kubernetes via the following options, which have been tailored for a self contained, fewer prerequisites, and well specified procedure:

- using K3s on an Ubuntu, RHEL, SLES machine or VM
- using Rancher Desktop running on Windows

## For installing Volt MX Go 

Follow the order for completing the procedures according to your preferred deployment option.

**When using K3s on an Ubuntu, RHEL, SLES machine or VM:**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).

2. [Install and configure K3s](deploykubernetes.md#install-and-configure-k3s).

3. [Complete preparatory procedure for installation of Volt MX Go](prereqindex.md#for-first-time-installation-of-volt-mx-go).

4. [Install Domino REST API](downloadhelmchart.md).

5. [Install MySql for Volt MX Go Foundry](installmysqlfoundry.md).

6. [Install Volt MX Go Foundry](installfoundry.md).

**When using Rancher Desktop running on Windows:**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).

2. [Install Rancher Desktop](deploykubernetes.md#install-rancher-desktop).

3. [Complete preparatory procedure for installation of Volt MX Go](prereqindex.md#for-first-time-installation-of-volt-mx-go).

4. [Install Domino REST API](downloadhelmchart.md).

5. [Install MySql for Volt MX Go Foundry](installmysqlfoundry.md).

6. [Install Volt MX Go Foundry](installfoundry.md).

## For upgrading an existing installation of Volt MX Go

1. [Complete preparatory procedure for upgrading an existing installation of Volt MX Go](prereqindex.md#for-upgrading-an-existing-installation-of-volt-mx-go).

2. [Upgrade Volt MX Go server components](versionupgrade1.md).

<!--## For moving from early access version to GA version of Volt MX Go

If you participated in the Early Access (EA) program, you need to perform the procedures to move to the GA version of Volt MX Go. 

!!!note
    The Early Access release doesn't support actual upgrades. You must remove the prior release deployment and install a new deployment to upgrade. This removes all the data from the prior release deployment.

1. [Complete preparatory procedure for moving from early access version to GA version of Volt MX Go](eatogamove.md).

2. [Install Domino REST API](downloadhelmchart.md).

3. [Install MySql for Volt MX Go Foundry](installmysqlfoundry.md).

4. [Install Volt MX Go Foundry](installfoundry.md).
-->

## Additional information

See [Helm and Kubectl commands](../references/kubecheatsheet.md) for more information.

## Next step

After completing the relevant procedures, proceed to [Install and upgrade Volt MX Go Iris](installirisindex.md).