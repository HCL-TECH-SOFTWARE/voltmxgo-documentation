# Install <!--and upgrade-->Volt MX Go v2.1 to development or test only environment

Perform a new <!--or an upgrade-->installation of Volt MX Go server components to a development or test only environment to allow you to try its different features in a safe environment. **This isn't intended for a production environment**.

!!!note
    Before starting the installation, make sure to verify that you meet the [System requirements](sysreqindex.md).

Starting with Volt MX Go v2.1, Volt MX Go components are now provided as plugins for installation on Volt Foundry and Volt Iris using the Volt MX Go Plugin Installer. Volt MX Go-specific versions of Foundry and Iris aren't available any more. With this change, users can use the Volt Foundry Single Container Solution with the Docker version of Domino REST API in their development or test-only environment. 

## For installing Volt MX Go

Follow the order for completing the procedures.

**When using Docker**

1. [Obtain authentication token from HCL Container Repository](../howto/obtainauthenticationtoken.md).
2. [Run Domino REST API with a Docker image](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/docker.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:15px;width:15px"}
3. [Install Volt MX Go Foundry using Volt Foundry Single Container Solution](installdrapi.md#for-single-container-solution)

<!--
**When using Kubernetes**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).
2. Run Domino REST API (procedure to be created)
3. [Install Volt MX Go Foundry using helm charts](nativeinstallers.md#for-using-helm-charts-on-a-supported-kubernetes-platform)
-->

## Next step

After completing the relevant procedures, proceed to [Install and upgrade Volt MX Go Iris](installirisindex.md).