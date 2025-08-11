# Volt MX Go v10

## Install Domino REST API

Guides you in installing Domino REST API.

### Before you begin

--8<-- "drapiversion.md"

### Procedure

1. Download the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/install/downloaddrapi.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Domino REST API documentation.

2. Follow the links to the installation procedure based on your preferred installation platform:

    - [For Windows](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/install/win.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    - [For Linux](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/install/linux.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

3. Complete all the [post-installation tasks](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/configuration/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.

For more information, see the [Installation and configuration](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} page in the [HCL Domino REST API documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.

## Install Volt Foundry

**Starting from Volt MX Go v10**, install the supported version of Volt Foundry using available installation mechanisms. The use of Helm charts and a single container solution are also supported for installing Volt Foundry.

**A Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work.**

### For using an installer

#### Before you begin

You have downloaded the Volt Foundry installer. **The minimum supported version is v10.0.1**.

For more information, see [Download HCL Volt MX Go installers](../portaldownload.md#for-volt-mx-go-v10).

#### Procedure

For installing Volt Foundry, click the link to the installation guide corresponding to your installation platform and follow the installation steps.

!!! warning "Important"

    - Make sure to check all the details and complete all the applicable procedures indicated in the sections in the installation guides.
    
    - After completing the installation, a Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation. 

- [For Windows](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_windows_install_guide/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For Linux](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_linux_install_guide/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

### For using Helm charts on a supported Kubernetes platform

#### Before you begin

- You have [obtained the authentication token from the HCL Container Repository](../../../howto/operation/obtainauthenticationtoken.md).
- You have completed all the installation [prerequisites](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#prerequisites "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
- You have reviewed the configuration parameters and identified their required values as you must provide them during the installation. For more information, see [Configuration](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#configuration "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
- You have downloaded the Volt Foundry Helm charts. **The minimum supported version is v10.0.1**.

    For more information, see [Download HCL Volt MX Go installers](../portaldownload.md#for-volt-mx-go-v10).

#### Procedure

1. Click the link to the installation guide and follow the installation steps.

    [Volt Foundry Container Helm installation guide](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#installation "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    !!! note 

        Make sure to check all the details and complete all the applicable steps indicated in the installation guide.
        

2. After completing all applicable steps in the installation guide, update the `values.yaml` file.

    1. Locate the `values.yaml` file in the Volt Foundry directory.
    2. Open the `values.yaml` file with your preferred editor and locate the line containing the `imageRegistry:` key.
    3. Change the value of the `imageRegistry:` key to `"hclcr.io/voltmxgo`.
    4. Save your changes and close the file.

3. Execute the `helm upgrade foundry` command to upgrade the running images to use Volt MX Go.


!!! warning "Important"

    After completing the installation, a Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation.

### For single container solution

For more information, see [Volt Foundry Single Container Solution](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the Volt MX Documentation.

#### Before you begin

- You have [obtained the authentication token from the HCL Container Repository](../../../howto/operation/obtainauthenticationtoken.md).
- You have completed all the [installation prerequisites](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html#prerequisites "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
- You have reviewed the configuration parameters and identified their required values as you must provide them during the installation. For more information, see [Configuration](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html#configuration "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
- You have downloaded the Volt Foundry Single Container install script. **The minimum supported version is v10.0.1**

    For more information, see [Download HCL Volt MX Go installers](../portaldownload.md#for-volt-mx-go-v10).

#### Procedure

1. Click the link to the installation guide and follow the installation steps.

    [Volt Foundry Single Container Solution installation guide](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html#installation "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    !!! note 

        - The installation guides indicate installation files and installation file download locations. You must use the installer you downloaded as indicated in the *Before you begin* section.
        - Make sure to check all the details and complete all the applicable steps indicated in the installation guide.

2. Update the `docker-compose.yml` file.

    1. Locate the `docker-compose.yml` file in the Volt Foundry directory.
    2. Open the `docker-compose.yml` file with your preferred editor and locate the line containing the `image:` key.
    3. Change the value of the `image:` key from `"hclcr.io/voltmx/voltmx-foundry-db:<version>_GA"` to `"hclcr.io/voltmxgo/voltmx-foundry-db:<version>_GA"`, wherein <version\> corresponds to the Volt Foundry release version. 

        For example, `"hclcr.io/voltmxgo/voltmx-foundry-db:10.0.0.1_GA"`.

    4. Save your changes and close the file. 

3. Stop the existing images by running the command `docker compose down`.
4. Restart the images by running the command `docker compose up -d`.

!!! warning "Important"

    After completing the installation, a Volt MX Go license must be used to activate Volt Foundry in the My HCLSoftware Portal for Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation.

## Next step

Before proceeding, make sure you have activated Volt Foundry using a Volt MX Go license in the My HCLSoftware Portal for the Volt MX Go features to work. For more information, see the [license activation guide](https://help.hcl-software.com/voltmx/v9.5/Foundry/voltmx_licensing_guide/Content/Volt_Foundry_Licensing_Guide.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} on the Volt MX documentation.

After completing the installation of **Domino REST API** and **Volt Foundry**, proceed to [Install Volt Iris](../installiris/irisv10.md).

