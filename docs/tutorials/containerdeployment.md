<!--# Install Volt MX Go via containerized deployment-->
# Install Volt MX Go to development or test only environment

The procedure intends to install Volt MX Go server components to a development or test only environment to allow you to try its different features in a safe environment. **This isn't intended for a production environment**.

The server components of Volt MX Go can be deployed with Kubernetes via the following options:

- using K3s on an Ubuntu, RHEL, SLES machine or VM
- using Rancher Desktop running on Windows

!!!note 
    <!-- Make sure that you have completed all the [prerequisite procedures](prerequisite.md) before proceeding with the following procedures.-->
    Before starting the installation, make sure to verify that you meet the [System requirements](sysreq.md).

### For installing Volt MX Go for the first time

Follow the order for completing the procedures according to your preferred deployment option.

**When using K3s on an Ubuntu, RHEL, SLES machine or VM:**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md)
1. [Install and configure K3s](k3sinstall.md)
2. [Complete preparatory procedure for installation of Volt MX Go](prereq.md)
3. [Install Domino REST API](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)


**When using Rancher Desktop running on Windows:**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md)
1. [Install Rancher Desktop](installrancher.md)
2. [Complete preparatory procedure for installation of Volt MX Go](prereq.md)
3. [Install Domino REST API](downloadhelmchart.md)
4. [Install MySql for Foundry](installmysqlfoundry.md)
5. [Install Foundry](installfoundry.md)

<!--### For upgrading an existing installation of Volt MX Go

!!!warning "Important"
    The Early Access release doesn't support actual upgrades. You must remove the prior release deployment and install a new deployment to upgrade. This removes all the data from the prior release deployment.

    The official product releases will support upgrades of existing deployments while maintaining existing deployment data.

1. [Complete preparatory procedure for upgrading existing installation of Volt MX Go](prereqnew.md)
2. [Install Domino REST API](downloadhelmchart.md)
3. [Install MySql for Foundry](installmysqlfoundry.md)
4. [Install Foundry](installfoundry.md)-->

### Additional information

See [FAQ and common procedures](../references/kubecheatsheet.md) for more information about Kubernetes commands.

After completing the procedures based on your preferred deployment option, proceed to [Install Volt MX Go Iris](installiris.md).