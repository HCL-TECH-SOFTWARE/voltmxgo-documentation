# System requirements for Volt MX Go v2.0.4 or earlier

This section describes the minimum system requirements for deploying Volt MX Go. 

## For installing Domino REST API

--8<-- "drapiversion.md"

Check the [system requirements](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0101789) for installing Domino REST API using the installer. 

## For installing Volt MX Go Foundry

**Software requirements**

Check the [Supported OS, Application Servers, and Database Guide](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Introduction.html) to know the software requirements for installing Volt MX Go Foundry using installers.

**Hardware requirements**

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Prerequisites.html#hardware-requirements)

- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Prerequisites.html#hardware-requirements)

**Network settings**

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Prerequisites.html#network-settings)

- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Prerequisites.html#network-settings)

**Supported browsers**

Check the [supported browsers](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Supported_Browsers.html) for the Volt MX Go Foundry Console.

**Prerequisites for Volt MX Go Foundry command line installer**

Check the additional [prerequisites](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html#prerequisites) when using the Foundry command line installer. 

**Prerequisites for Volt MX Foundry Containers Helm Installation**

Check the [prerequisites](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#prerequisites) when using the Volt MX Go Foundry Containers Helm Installation. 

## For installing Volt MX Go Iris

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

    [Supported macOS versions](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_mac/Content/Supported_VoltMX_Iris_MacOS_versions.html) 

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

!!!note
    - For more information on K3s, see [K3s - Lightweight Kubernetes](https://docs.k3s.io/).
    
    - For more information on the installation requirements for K3s, see [K3s Installation Requirements](https://docs.k3s.io/installation/requirements).

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
    - For more information on Rancher Desktop, see [Introduction](https://docs.rancherdesktop.io/) in the Rancher Desktop documentation. 
    
    - For more information on Rancher Desktop installation requirements, see [Installation](https://docs.rancherdesktop.io/getting-started/installation/#windows) in the Rancher Desktop documentation.

## Next step

Proceed to [Installation](../tutorials/installation.md).