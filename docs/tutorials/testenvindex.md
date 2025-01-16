# Install <!--and upgrade-->Volt MX Go v2.1 to development or test only environment

Perform a new or an upgrade installation of Volt MX Go server components to a development or test only environment to allow you to try its different features in a safe environment. **This isn't intended for a production environment**.

!!!note
    Before starting the installation, make sure to verify that you meet the [System requirements](sysreqindex.md).


The server components of Volt MX Go can be deployed with Docker<!--or Kubernetes-->.

## For installing Volt MX Go

Follow the order for completing the procedures<!-- according to your preferred deployment option-->. 

**When using Docker**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).
2. [Run Domino REST API with a Docker image](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/docker.html)
3. [Install Volt MX Go Foundry using Volt Foundry Single Container Solution](installdrapi.md#for-single-container-solution)

<!--
**When using Kubernetes**

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).
2. Run Domino REST API (procedure to be created)
3. [Install Volt MX Go Foundry using helm charts](nativeinstallers.md#for-using-helm-charts-on-a-supported-kubernetes-platform)
-->

## Next step

After completing the relevant procedures, proceed to [Install and upgrade Volt MX Go Iris](installirisindex.md).