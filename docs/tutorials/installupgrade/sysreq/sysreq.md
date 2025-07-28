# System requirements for Volt MX Go v2.0.4 or earlier - EOS

--8<-- "endofsupport.md"

This section describes the minimum system requirements for deploying Volt MX Go.

## For installing Domino REST API

--8<-- "drapiversion.md"

Check the [system requirements](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0101789 "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} for installing Domino REST API using the installer.

## For installing Volt Foundry

**Software requirements**

Check the [Supported OS, Application Servers, and Database Guide](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} to know the software requirements for installing Volt Foundry using installers.

**Hardware requirements**

- [For Windows](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_windows_install_guide/Content/Prerequisites.html#hardware-requirements "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For Linux](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_linux_install_guide/Content/Prerequisites.html#hardware-requirements "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

**Network settings**

- [For Windows](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_windows_install_guide/Content/Prerequisites.html#network-settings "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For Linux](https://help.hcl-software.com/voltmx/v10/Foundry/voltmx_foundry_linux_install_guide/Content/Prerequisites.html#network-settings "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

**Supported browsers**

Check the [supported browsers](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Supported_Browsers.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} for the Volt Foundry Console.

**Prerequisites for Volt Foundry command line installer**

Check the additional [prerequisites](https://help.hcl-software.com/voltmx/v10/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html#prerequisites "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} when using the Foundry command line installer.

**Prerequisites for Volt MX Foundry Containers Helm Installation**

Check the [prerequisites](https://help.hcl-software.com/voltmx/v10/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#prerequisites "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} when using the Volt Foundry Containers Helm Installation.

## For installing Volt Iris

=== "On Windows"

    **Operating System**

    Windows 11, Windows 10, Windows 8.1 Update. Supports 64-bit Operating Systems

    **Hardware**

    |Component	|Requirement|
    |-----------|-----------|
    |Processor and Architecture	|Dual Core processor, 64-bit|
    |RAM	    |8 GB |
    |Internal Storage	|2 GB|
    |Network	|Ethernet Port|

=== "On Mac"

    **Operating System**

    [Supported macOS versions](https://help.hcl-software.com/voltmx/v10/Iris/iris_starter_install_mac/Content/Supported_VoltMX_Iris_MacOS_versions.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} 

    **Hardware**

    |Component	|Requirement |
    | --------  | -----------|       
    |Processor	|x86-64 CPU, M1/M2 CPU<br/>(64-bit Mac with an Intel Core i3, i5, i7, Intel Xeon processor or M1, M2 ARM processor)|
    |RAM	    |8 GB |
    |Internal Storage|	24 GB|
    |Network Ethernet |Port|

## For deploying Volt MX Go using K3s on an Ubuntu, RHEL, SLES machine, or VM

--8<-- "devtestenvironment.md"

**Operating System**

- RHEL9
- Ubuntu
- SLES

**Hardware** 

| Spec | Minimum |
| ---- | ------- |
| CPU | 4 cores |
| RAM | 16 GB |

!!! note

    - For more information on K3s, see [K3s - Lightweight Kubernetes](https://docs.k3s.io/ "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
    
    - For more information on the installation requirements for K3s, see [K3s Installation Requirements](https://docs.k3s.io/installation/requirements "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.

## For deploying Volt MX Go using Rancher Desktop running on Windows

--8<-- "devtestenvironment.md"

**Operating System**

- Windows 10 build 1909 or higher
- Windows 11

**Hardware**

| Spec | Minimum |
| ---- | ------- |
| CPU | 4 cores |
| RAM | 32 GB |

**Additional requirements**

Rancher Desktop requires the following on Windows:

- Running on a machine with virtualization capabilities.
- Persistent internet connection.
- Windows Subsystem for Linux on Windows. This will automatically be installed as part of the Rancher Desktop setup. Manually downloading a distribution isn't necessary.

!!!note
    - For more information on Rancher Desktop, see [Introduction](https://docs.rancherdesktop.io/ "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the Rancher Desktop documentation.

    - For more information on Rancher Desktop installation requirements, see [Installation](https://docs.rancherdesktop.io/getting-started/installation/#windows "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the Rancher Desktop documentation.

## Next step

- To install the server components of Volt MX Go, proceed to [Install Volt MX Go server components](../installserver/index.md).

- To upgrade the server components of Volt MX Go, proceed to [Upgrade Volt MX Go server components](../upgradeserver/index.md).

- To install and upgrade Volt Iris, proceed to [Install and upgrade Volt Iris](../installiris/index.md).
