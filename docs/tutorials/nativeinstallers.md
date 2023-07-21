<!--# Install Volt MX Go via installers-->
# Install Volt MX Go server components

The following server components of Volt MX Go are deployed using installers:

- Volt MX Go Foundry
- Domino REST API

!!!warning "Important"
    - Using this installation option would require you to use your own Domino server.
    - Before starting the installation, make sure to verify that you meet the [System requirements](sysreq.md). 
    

## Install Domino REST API

1. Downloaded the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html#download-the-domino-rest-api){: target="_blank"}.
2. Follow the links to the installation procedure based on your preferred installation platform:

    - [For Windows](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/win.html){: target="_blank"}
    - [For Linux](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/linux.html){: target="_blank"}

3. Complete all the [post-installation tasks](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/postinstallation.html){: target="_blank"}.

For more information, see the [Installation and configuration](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html){: target="_blank"} page in the Domino REST API documentation.


## Install Volt MX Go Foundry

Volt MX Go Foundry supports the following installation mechanisms:

- Use the Windows or Linux installers that use Install Anywhere to do the installation. It allows you to install a bundled Tomcat or JBoss app server or install it onto an existing app server (JBOSS single or multi-node, or WebLogic).
- Use the Command Line installer for advanced deployments.
- Use helm charts on one of the supported Kubernetes platforms, including OpenShift, AKS (Azure), EKS (AWS), and GKE (Google).

### For using an installer

1. Download the Volt MX Go Foundry installer based on your preferred installation platform/option.

    For more information, see [Download HCL Volt MX Go Release package](portaldownload.md).

2. Extract the installer from the downloaded ZIP file. 
3. Follow the links to the installation guides based on your preferred installation platform/option:

    !!!warning "Important"
        - The installation guides will indicate installation files and installation file download locations. **You must use the installer you downloaded in Step 1.**
        - Make sure to check all the details and complete all the applicable procedures indicated in the sections in the installation guides. 

    - [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Introduction.html){: target="_blank"}
    - [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Introduction.html){: target="_blank"}
    - [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html){: target="_blank"}

### For using helm charts on a supported Kubernetes platform

1. [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md).
2. Follow all the steps in the [Installation Guide for Volt MX Foundry Containers Helm Installation](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Introduction.html){: target="_blank"}.

!!!warning "Important"
        The installation guide will indicate installation files and installation file download locations. **You must use the helm charts downloaded from the [HCL Container Repository](https://hclcr.io){: target="_blank"}**.
    

## Additional information

After completing the installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install Volt MX Go Iris](installiris.md).

