# Volt MX Go v10

Guides you in upgrading Volt MX Go server components.

## Upgrade Domino REST API

### Before you begin

--8<-- "drapiversion.md"

### Procedure

1. Download the required version of the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/install/downloaddrapi.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Domino REST API documentation.

2. Follow the relevant steps in the [upgrade procedure](https://opensource.hcltechsw.com/Domino-rest-api/howto/production/versionupdate.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the [HCL Domino REST API documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} based on your installation platform.

## Upgrade Volt Foundry

The following procedures guide you in upgrading Volt Foundry to the latest version. As Volt Foundry supports various installation mechanisms, refer to the relevant upgrade procedure.

### For using an installer

The upgrade process works by upgrading the existing database to the latest version, and installing fresh application server artifacts, such as data sources and WARs. For installation details such as hostname, database port, prefix, suffix, you must refer to the installation logs of your previous setup.

The installer doesn't support automatic backups of database and other artifacts. You must clean up the existing application server artifacts and take a backup of the custom artifacts. The installer also doesn't support rollback in case of a failure during the upgrade. To roll back, restore the database and server artifacts you backed up before upgrading.

<!--Upgrades Volt Foundry from Volt MX Go v2.0.4 to Volt MX Go v2.1.-->

#### Before you begin

- Back up your databases and server artifacts.

- Download the latest Volt Foundry installer based on your installation platform. **The minimum supported version is v10.0.1**. For more information, see [Download HCL Volt MX Go installers](../portaldownload.md#for-volt-mx-go-v10).

- Ensure that the Volt Foundry installer has execute permission.
- Ensure that you have the path of your previous installation directory.
- Ensure that you stop the application server of your existing Volt Foundry instance, which you want to upgrade.

#### Install Volt Foundry

- Follow the link to the upgrade procedure based on your used installation platform. 

    !!! warning "Important"

        - Volt Foundry must be licensed with a Volt MX Go entitlement for the Volt MX Go features to work.
        - The upgrade procedure indicates installation files and installation file download locations. **You must use the installer you downloaded in *Before you begin*.**
        - Check all the details and complete all the applicable steps indicated in the upgrade procedure.
        - Make sure to point to the same database you used for your previous Volt Foundry installation to access all the projects you worked on.
        
        - After completing the installation, a Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation. 

    - [For Windows](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_windows_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    - [For Linux](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_linux_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}
    <!-- [For command line installer](https://help.hcl-software.com/voltmx/v10/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html)-->


### For using Helm charts on a supported Kubernetes platform

#### Before you begin

You have downloaded the Volt Foundry Helm charts. For more information, see [Download HCL Volt MX Go installers](../portaldownload.md#for-volt-mx-go-v10).

#### Procedure

1. Click the link to the upgrade guide based on your requirement and follow the steps. 

    - [Upgrade Individual Foundry Components](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html#how-to-upgrade-individual-foundry-components "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    - [Upgrade All Foundry Components](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html#how-to-upgrade-all-foundry-components "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    !!! warning "Important"

        Make sure to check all the details and complete all the applicable steps indicated in the installation guide.

2. After completing all applicable steps in the installation guide, update the `values.yaml` file.

    1. Locate the `values.yaml` file in the Volt Foundry directory.
    2. Open the `values.yaml` file with your preferred editor and locate the line containing the `imageRegistry:` key.
    3. Change the value of the `imageRegistry:` key to `hclcr.io/voltmxgo`.
    4. Save your changes and close the file.

3. Execute the `helm upgrade foundry` command to upgrade the running images to use Volt MX Go.

!!! warning "Important"

    After completing the installation, a Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation.
    
## Next step

Before proceeding, make sure you have activated Volt Foundry using a Volt MX Go license in the My HCLSoftware Portal for the Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation.

After completing the upgrade installation of **Domino REST API** and **Volt Foundry**, proceed to [Install and upgrade Volt Iris](../installiris/index.md).
