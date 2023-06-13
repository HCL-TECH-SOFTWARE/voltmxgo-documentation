# System requirements

This section describes the minimum system requirements for deploying the Early Access version of Volt MX Go. 

## For deploying Volt MX GO using K3s on an Ubuntu, RHEL, SLES machine, or VM

!!!note
    - For more information on K3s, see [K3s - Lightweight Kubernetes](https://docs.k3s.io/){: target="_blank"}.
    - For more information on the installation requirements for K3s, see [K3s Installation Requirements](https://docs.k3s.io/installation/requirements){: target="_blank"}.

### Operating System

- RHEL9
- Ubuntu
- SLES

### Hardware 

| Spec | Minimum |
| ---- | ------- |
| CPU | 4 cores |
| RAM | 16 GB |

## For deploying Volt MX Go using Rancher Desktop running on Windows

!!!note
    - For more information on Rancher Desktop, see [Introduction](https://docs.rancherdesktop.io/){: target="_blank"}.
    
    - For more information on Rancher Desktop installation requirements, see [Installation](https://docs.rancherdesktop.io/getting-started/installation/#windows){: target="_blank"}.

### Operating System

- Windows 10 build 1909 or higher
- Windows 11

### Hardware

| Spec | Minimum |
| ---- | ------- |
| CPU | 4 cores |
| RAM | 32 GB |

### Additional requirements

Rancher Desktop requires the following on Windows:

- Running on a machine with virtualization capabilities.
- Persistent internet connection.
- Windows Subsystem for Linux on Windows. This will automatically be installed as part of the Rancher Desktop setup. Manually downloading a distribution isn't necessary.


## For installing Volt MX Go Foundry using native installers

### Software requirements
Check the [Supported OS, Application Servers, and Database Guide](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Introduction.html){: target="_blank"} to know the software requirements for installing Volt MX Go Foundry using native installers.

### Hardware requirements

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Prerequisites.html#hardware-requirements){: target="_blank"}
- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Prerequisites.html#hardware-requirements){: target="_blank"}

### Network settings

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Prerequisites.html#network-settings){: target="_blank"}
- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Prerequisites.html#network-settings){: target="_blank"}

### Supported browsers
Check the [supported browsers](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_supported_devices_os_browsers/Content/Supported_Browsers.html){: target="_blank"} for the Volt MX Go Foundry Console.

## For installing Domino REST API using native installer

Check the [system requirements](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0101789){: target="_blank"} for installing Domino REST API using the native installer. 

## For installing Volt MX Go Iris on Windows

### Operating System

Windows 11, Windows 10, Windows 8.1 Update. Supports 64-bit Operating Systems

Installer File (mandatory)

### Hardware

|Component	|Requirement|
|-----------|-----------|
|Processor and Architecture	|Dual Core processor, 64-bit|
|RAM	    |8 GB |
|Internal Storage	|2 GB|
|Network	|Ethernet Port|


## For installing Volt MX Go Iris on Mac

### Operating System

Mac OS X 10.9 and above

### Hardware

|Component	|Requirement |
| --------  | -----------|       
|Processor	|x86-64 CPU, M1/M2 CPU<br/>(64-bit Mac with an Intel Core i3, i5, i7, Intel Xeon processor or M1, M2 ARM processor)|
|RAM	    |8 GB |
|Internal Storage|	24 GB|
|Network Ethernet |Port|

## Next step

Proceed to [Installation](../tutorials/installation.md).