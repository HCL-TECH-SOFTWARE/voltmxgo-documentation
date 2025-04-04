# For Volt MX Go v2.0.4 or earlier

## Install Domino REST API

Guides you in installing Domino REST API.

### Before you begin

--8<-- "drapiversion.md"

### Procedure

1. Download the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html#download-the-domino-rest-api "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Domino REST API documentation.

2. Follow the links to the installation procedure based on your preferred installation platform:

    - [For Windows](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/win.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}

    - [For Linux](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/linux.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}

3. Complete all the [post-installation tasks](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/postinstallation.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}.

For more information, see the [Installation and configuration](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} page in the [HCL Domino REST API documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}.

## Install Volt MX Go Foundry

Volt MX Go Foundry supports the following installation mechanisms:

- Use the Windows or Linux installers that use Install Anywhere to do the installation. It allows you to install a bundled Tomcat or JBoss app server or install it onto an existing app server (JBOSS single or multi-node, or WebLogic).
- Use the Command Line installer for advanced deployments.
- Use helm charts on one of the supported Kubernetes platforms, including OpenShift, AKS (Azure), EKS (AWS), and GKE (Google).

### For using an installer

#### Before you begin

You have downloaded the latest version of Volt MX Go Foundry installer based on your preferred installation platform/option. For more information, see [Download HCL Volt MX Go installers](portaldownload.md#for-volt-mx-go-v204-and-earlier).

#### Procedure <!--Install Volt MX Go Foundry-->

For installing Volt MX Go Foundry, click the link to the installation guide corresponding to your installation platform and follow the installation steps.

!!!warning "Important"
    - The installation guides indicate installation files and installation file download locations. **You must use the installer you downloaded as indicated in the *Before you begin* section.**
    - Make sure to check all the details and complete all the applicable procedures indicated in the sections in the installation guides.

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}

### For using helm charts on a supported Kubernetes platform

#### Before you begin
  
!!!note "Prerequisite"
    [Obtain authentication token from HCL Container Repository](../howto/operation/obtainauthenticationtoken.md) before proceeding.

#### Procedure

1. Create a namespace and a temp directory for the charts.

    Run the following commands to create a namespace, set the current context to **mxgo**, create a temp directory for downloading the charts, and make it the current directory:

    ```
    kubectl create namespace mxgo
    kubectl config set-context --current --namespace=mxgo
    mkdir ~/mxgo
    cd ~/mxgo
    ```

    --8<-- "restartwindows.md"

2. Configure Helm to pull from HCL Container Repository.

    The procedure sets up Helm with the details necessary to authenticate with the HCL Container Repository. You will need your [email and authentication token](../howto/operation/obtainauthenticationtoken.md) used with the HCL Container Repository.

    - Run the following command to set up Helm:

        ```
        helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
        ```

        !!! example

            `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`

        !!! note

            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](../howto/obtainauthenticationtoken.md) as your authentication token or password.

        If you get an error message similar to the following:

        ``` { .yaml .no-copy }
        Error: looks like https://hclcr.io/chartrepo/voltmxgo is not a valid chart repository or cannot be reached: failed to fetch https://hclcr.io/chartrepo/voltmxgo/index.yaml : 401 Unauthorized
        ```

        Most likely, you haven't specified your username or authentication token correctly. Make sure the case and content matches exactly what's listed on the HCL Container Repository site and retry.

3. Download Foundry charts.

    1. Run the following command to make sure that the chart information for the repositories is up-to-date.

        ```
        helm repo update
        ```

        --8<-- "helmversion.md"

    2. Run the following commands to download the Foundry charts, unpack the files, and move the `values.yaml` file to the current directory:

        ```
        mkdir foundry
        cd foundry
        helm pull hclcr/voltmx-dbupdate
        helm pull hclcr/voltmx-foundry
        tar -xzf voltmx-foundry-1.n.n.tgz
        tar -xzf voltmx-dbupdate-1.n.n.tgz
        mv voltmx-foundry/values.yaml  ./
        mv voltmx-foundry/init-guids.sh  ./
        chmod +x init-guids.sh
        ```
        !!! note
        
            The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.


    3. Volt MX Go Foundry uses several Global Unique IDs to distinguish different installations of Volt MX Go Foundry. Invoke the init-guids script to generate the IDs using the following command:

        ```
        ./init-guids.sh --new
        ```

    4. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and `your-authentication-token` with your [email and authentication token](../howto/operation/obtainauthenticationtoken.md) used with the HCL Container Repository.

        ```{ .yaml .no-copy }
        imageCredentials:
        username: your-email
        password: your-authentication-token
        ```

        !!! note

            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](../howto/obtainauthenticationtoken.md) as your authentication token or password.

    5. Locate the following line in the file and add your Volt MX Go Foundry server domain name setting:

        ```{ .yaml .no-copy }
        serverDomainName:
        ```
        
        Whatever server domain name you specify here, you need to ensure that it's resolvable. There is no additional work if you have already registered your server domain name in DNS. However, if you haven't registered it, you must add it to the server's `/etc/hosts` file<!--[Ensure Foundry Hostnames are resolvable](prereqindex.md#for-first-time-installation-of-volt-mx-go)-->, substituting your server domain name. Additionally, you must make the same updates in k3s's coredns config map <!--as described in [For K3s only](prereqindex.md#for-first-time-installation-of-volt-mx-go)-->and substituting your server domain name.

    6. Locate the following lines in the file and add your Volt MX Go Foundry database details:

        ```{ .yaml .no-copy }
        ### Database details ###

        # Database type which you want to use for Volt MX Go Foundry (String)
        # Possible values:
        #   "mysql" for MySQL DB server
        #   "sqlserver" for Azure MSSQL or SQLServer
        #   "oracle" for Oracle DB server
        dbType:

        # Database server hostname (String)
        dbHost:

        # Database server port number (Number). This can be empty for cloud managed service.
        dbPort:

        # Database User and password - you may set a single general userid/password here,
        # or you may set specific userid/password combinations below.  If set, the
        # specific values override the general dbUser/dbPass.

        # Database server user (String)
        dbUser:

        # Database server password (String) enclosed in quotes
        dbPass:
        ```

    7. For more advanced configuration options, see [Configuration](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#configuration "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} in the *Installation Guide for Volt MX Foundry Containers Helm Installation*.

    8. Save the file and exit.

4. (Optional) Perform advanced scenario procedures.

    Perform the procedures under [Advanced Scenarios](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Advanced_Scenarios.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}.


5. Deploy Foundry's dbupdate to create the databases.

    1. Run the following Helm install command to deploy Foundry's dbupdate:

        ```
        helm install dbupdate voltmx-dbupdate -f values.yaml
        ```

    2. Run the following command to verify deployment completion of Foundry's dbupdate:

        ```
        kubectl get pods -o wide -w
        ```

        The output should be similar to the following and will update over time:

        ```{ .yaml .no-copy }
        NAME                            READY   STATUS      RESTARTS   AGE
        domino-drapi-6d755b68df-2sfhb   3/3     Running     0          6m13s
        mysql-0                         1/1     Running     0          2m37s
        foundry-db-update-dzdrx         1/1     Running     0          24s
        foundry-db-update-dzdrx         0/1     Completed   0          65s
        foundry-db-update-dzdrx         0/1     Completed   0          67s
        foundry-db-update-dzdrx         0/1     Completed   0          68s
        ```

    3. Once the foundry-db-update pod shows Completed in the STATUS column, the databases have been created. Press `Ctrl-c` to stop the kubectl command.

6. Install Volt MX Go Foundry.

    1. Run the following Helm install command to deploy Volt MX Go Foundry:

        ```
        helm install foundry voltmx-foundry -f values.yaml
        ```

    2. Run the following command to verify when the Volt MX Go Foundry install is ready:

        ```
        kubectl get pods -o wide -w
        ```

        The output should be similar to the following and will update over time:

        ![output](../assets/images/output1.png)


    3. Monitor all the foundry pods except for the foundry-db-update pod as it has already been completed. Once the other foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.

    **Volt MX Go Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/)**.

    !!!note
        - If you defined a different Volt MX Go Foundry hostname, the Foundry URL would be the defined Foundry hostname concatenated with `/mfconsole/`.
        - If you want to access this deployment from a remote machine, you most likely need to update the `/etc/hosts` file on the remote machine as well.
        
        - To create an account, see [Create a Volt MX Go Foundry administrator account](../howto/foundryadminaccount.md).
        
        - To connect to Domino server from your Notes client, see [Connect to Domino server from your Notes client](../howto/connectdominofromnotes.md).


7. (Optional) Perform monitoring procedures.

    Perform the procedures under [Monitoring](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Monitoring.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX documentation.

    !!!note
        The procedures are for enabling important monitoring features such as Metrics Server, Elastic Stack, Kuberhealthy.

8. (Optional) Perform post installation tasks.

    Perform the procedures under the [Post Installation Tasks](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX documentation.

## Next step

After completing the installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install Volt MX Go Iris](upgradeiris.md).

<!--# Install Volt MX Go Foundry

## Overview

**Starting from Volt MX Go v2.1 release**, Volt MX Go Foundry is enabled by installing the minimum required version of Volt Foundry using available installation mechanisms and then installing Volt MX Go plugins to Volt Foundry using a Volt MX Go Plugin Installer. The use of helm charts and a single container solution are also supported for installing Volt Foundry. An important thing to note for Volt MX Go v2.1 is that **only Volt Foundry using a Tomcat non-clustered application server is supported**. 

**For earlier releases up to Volt MX Go v2.0.4 release**, Volt MX Go Foundry supports the following installation mechanisms:

- Use the Windows or Linux installers that use Install Anywhere to do the installation. It allows you to install a bundled Tomcat or JBoss app server or install it onto an existing app server (JBOSS single or multi-node, or WebLogic).
- Use the Command Line installer for advanced deployments.
- Use helm charts on one of the supported Kubernetes platforms, including OpenShift, AKS (Azure), EKS (AWS), and GKE (Google).

## For using an installer

### For Volt MX Go v2.1

#### Before you begin

- You have downloaded the Volt Foundry installer. The minimum required version is v9.5.18.0.   
- You have downloaded the Volt MX Go Plugin Installer. 

For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v21).

#### 1. Install Volt Foundry

For installing Volt MX Go Foundry, click the link to the installation guide corresponding to your installation platform and follow the installation steps. 

!!!warning "Important"
    - For Volt MX Go v2.1, **only Volt Foundry using a Tomcat non-clustered application server is supported**.
    - Make sure to check all the details and complete all the applicable procedures indicated in the sections in the installation guides.

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Introduction.html)
    
- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Introduction.html)

#### 2. Install Volt MX Go Plugin Installer

The procedure enables the installation of the Volt MX Go Plugin Installer, which is used for installing the Volt MX Go plugins to Volt Foundry.

=== "on Linux"

    1. Open terminal.
    1. Navigate to the directory containing the `VoltMXGoInstallationTool.bin` to ensure that you are in the right location to execute the installation commands for the bin file. 
    1. Enter the following command to grant executable permissions to the `VoltMXGoInstallationTool.bin` file and press **Enter**. 

	    `sudo chmod +x VoltMXGoInstallationTool.bin`

	    Using the `chmod` command with `sudo` ensures administrative privileges.

    1. Run the `VoltMXGoInstallationTool.bin` file to start the installation using the following command and press **Enter**.

	    `./VoltMXGoInstallationTool.bin`

    1. Follow the installation instructions. The binary file will initiate the installation process and may prompt you with on-screen instructions. Follow these instructions carefully to complete the installation.

        !!!note
            If you have a graphical terminal associated with your Linux deployment, the **Volt MX Go Installation Tool** window opens. Otherwise, installation is via the command line.  

    <!--1. Enter `ls -latrh` to list the installation directory contents to identify the shortcuts for running and uninstalling the installer.
    1. Take note of the shortcut for running the installer.

=== "on Windows"

    1. Navigate to the folder containing the downloaded installer file. 
    1. Double-click the *VoltMXGoInstallationTool.exe* installer file. The **Volt MX Go Installation Tool** window opens. 
    1. On the **Introduction**, read the details and instructions, and then click **Next**.
    1. On the **License Agreement**, read the agreement details, select the **I accept the terms of the License agreement** checkbox, and then click **Next**.
    1. On the **Choose Install Folder**, click **Next** if you agree with the indicated default location. 

        !!!tip
            - If you want a different installation location, click **Choose** to select your preferred installation location or directly enter your preferred installation location in the text box, and then click **Next**.
            - If you selected a different installation location and decided to revert to the default location, click **Restore Default Folder** and then click **Next**.

    1. On the **Pre-Installation Summary**, review the details and then click **Install**.
    1. On the **Installing**, see the installation status.
    1. On the **Install Complete**, click **Done**.

#### 3. Install Volt MX Go plugins

The procedure enables the installation of Volt MX Go plugins to Volt Foundry to enable Volt MX Go features.

!!!warning "Important"
    - For Volt MX Go v2.1, **you can only install Volt MX Go plugins to Volt Foundry that uses a Tomcat non-clustered application server**.

=== "on Linux"

    1. Open Terminal.
    1. Go to the directory where you installed the Volt MX Go Plugin Installer. By default, the installer executable is located in the `~/VoltMXGoPluginInstaller` directory.
    2. Run the Volt MX Go Plugin Installer by entering the following command and press **Enter**.

        `./VoltMXGoPluginInstaller`

        The installation tool opens on the Terminal.

    3. Enter **1** to install Volt MX Go plugins in Volt Foundry and press **Enter**.
    4. Specify the Tomcat WebApps directory by entering the number corresponding to your installation or enter the full path to your Tomcat WebApps directory, and then press **Enter**.

        You get a confirmation statement that the plugins have been installed.

    6. Enter **7** and press **Enter** to exit the installation tool. 

=== "on Windows"

    1. Select **Start**, scroll through the alphabetical list, and select **Volt MX Go Plugin Installer**. Depending on your OS, you might need to select **All apps**, scroll through the alphabetical list, and click **Volt MX Go Plugin Installer**.

        OR

        Double-click the **Volt MX Go Plugin Installer** shortcut on your desktop if available. 

        A Command Prompt window opens.

    2. Enter **1** to install Volt MX Go plugins and press **Enter**.
    3. Specify the Tomcat WebApps directory by entering the number corresponding to your installation, or enter the full path to your Tomcat WebApps directory, then press **Enter**. 

        You get a confirmation statement that the plugins have been installed. 

    5. Press **Enter** to close the Command Prompt window.

### For Volt MX Go v2.0.4 or earlier

#### Before you begin

You have downloaded the latest version of Volt MX Go Foundry installer based on your preferred installation platform/option. For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v204-or-earlier).

#### Install Volt MX Go Foundry

For installing Volt MX Go Foundry, click the link to the installation guide corresponding to your installation platform and follow the installation steps. 

!!!warning "Important"
    - The installation guides indicate installation files and installation file download locations. **You must use the installer you downloaded as indicated in the *Before you begin* section.**
    - Make sure to check all the details and complete all the applicable procedures indicated in the sections in the installation guides.

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Introduction.html)
    
- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Introduction.html)
    
- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html)

## For using helm charts on a supported Kubernetes platform
  
!!!note "Prerequisite"
    [Obtain authentication token from HCL Container Repository](obtainauthenticationtoken.md) before proceeding.

### For Volt MX Go v2.1

#### Before you begin

- You have completed all the installation [prerequisites](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#prerequisites).
- You have reviewed the configuration parameters and identified their required values as you must provide them during the installation. For more information, see [Configuration](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#configuration).
- You have downloaded the Volt Foundry Helm charts. For more information, see [Download HCL Volt MX Go Release package](./portaldownload.md#for-volt-mx-go-v21). 

#### Install Volt Foundry

1. Click the link to the installation guide and follow the installation steps. 

    [Volt Foundry Container Helm installation guide](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#installation)

    !!!warning "Important"
        Make sure to check all the details and complete all the applicable steps indicated in the installation guide.

2. After completing all applicable steps in the installation guide, update the `values.yaml` file.

    1. Locate the `values.yaml` file in the Volt Foundry directory.
    2. Open the `values.yaml` file with your preferred editor and locate the line containing the `imageRegistry:` key.
    3. Change the value of the `imageRegistry:` key to `"hclcr.io/voltmxgo`.
    4. Save your changes and close the file. 

3. Execute the `helm upgrade foundry` command to upgrade the running images to use Volt MX Go. 


!!!note
    Starting with Volt MX Go v2.1, only one helm chart `voltmx-foundry` is used for Volt MX Go Foundry installation.

1. Create a namespace and a temp directory for the charts.

    Run the following commands to create a namespace, set the current context to **mxgo**, create a temp directory for downloading the charts, and make it the current directory:

    ```
    kubectl create namespace mxgo
    kubectl config set-context --current --namespace=mxgo
    mkdir ~/mxgo
    cd ~/mxgo
    ```

    --8<-- "restartwindows.md"

2. Configure Helm to pull from HCL Container Repository.

    The step sets up Helm with the details necessary to authenticate with the HCL Container Repository. You will need your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

    - Run the following command to set up Helm:

        ```
        helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
        ```

        !!!example
            `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`


        !!!note
            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

        If you get an error message similar to the following:

        ``` { .yaml .no-copy }
        Error: looks like https://hclcr.io/chartrepo/voltmxgo is not a valid chart repository or cannot be reached: failed to fetch https://hclcr.io/chartrepo/voltmxgo/index.yaml : 401 Unauthorized
        ```

        Most likely, you haven't specified your username or authentication token correctly. Make sure the case and content matches exactly what's listed on the HCL Container Repository site and retry.

3. Download Foundry chart.

    1. Run the following command to make sure that the chart information for the repositories is up-to-date.

        ```
        helm repo update
        ```

        --8<-- "helmversion.md"

    2. Run the following commands to download the Foundry chart, unpack the files, and move the `values.yaml` file to the current directory:

        ```
        mkdir foundry
        cd foundry
        helm pull hclcr/voltmx-foundry
        tar -xzf voltmx-foundry-1.n.n.tgz
        mv voltmx-foundry/values.yaml  ./
        mv voltmx-foundry/init-guids.sh  ./
        chmod +x init-guids.sh
        ```
        !!!note
            The chart name has a version string in the filename. The `helm pull` command will pull down the latest version of the chart. Ensure your tar command uses the correct matching filename.


    3. Volt MX Go Foundry uses several Global Unique IDs to distinguish different installations of Volt MX Go Foundry. Invoke the init-guids script to generate the IDs using the following command:
    
        ```
        ./init-guids.sh --new
        ```

    4. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and `your-authentication-token` with your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

        ```{ .yaml .no-copy }
        imageCredentials:
        username: your-email
        password: your-authentication-token
        ```

        !!!note
            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

    5. Locate the following line in the file and add your Volt MX Go Foundry server domain name setting:

        ```{ .yaml .no-copy }
        serverDomainName:
        ```
        
        Whatever server domain name you specify here, you need to ensure that it's resolvable. There is no additional work if you have already registered your server domain name in DNS. However, if you haven't registered it, you must add it to the server's /etc/hosts file [Ensure Foundry Hostnames are resolvable](prereqindex.md#for-first-time-installation-of-volt-mx-go), substituting your server domain name. Additionally, you must make the same updates in k3s's coredns config map as described in [For K3s only](prereqindex.md#for-first-time-installation-of-volt-mx-go) again substituting your server domain name.

    6. Locate the following lines in the file and add your Volt MX Go Foundry database details:

        ```{ .yaml .no-copy }
        ### Database details ###

        # Database type which you want to use for Volt MX Go Foundry (String)
        # Possible values:
        #   "mysql" for MySQL DB server
        #   "sqlserver" for Azure MSSQL or SQLServer
        #   "oracle" for Oracle DB server
        dbType:

        # Database server hostname (String)
        dbHost:

        # Database server port number (Number). This can be empty for cloud managed service.
        dbPort:

        # Database User and password - you may set a single general userid/password here,
        # or you may set specific userid/password combinations below.  If set, the
        # specific values override the general dbUser/dbPass.

        # Database server user (String)
        dbUser:

        # Database server password (String) enclosed in quotes
        dbPass:
        ```

    7. For more advanced configuration options, see [Configuration](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#configuration) in the *Installation Guide for Volt MX Foundry Containers Helm Installation*.

    8. Save the file and exit.

4. (Optional) Perform advanced scenario procedures.

    Perform the procedures under [Advanced Scenarios](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Advanced_Scenarios.html).


5. Install Volt MX Go Foundry.

    1. Run the following Helm install command to deploy Volt MX Go Foundry:

        ```
        helm install foundry voltmx-foundry -f values.yaml
        ```

    2. Run the following command to verify when the Volt MX Go Foundry install is ready:

        ```
        kubectl get pods -o wide -w
        ```

        The output should be similar to the following and will update over time:

        ![output](../assets/images/output11.png)

    3. Monitor all the foundry pods and the foundry-db-update pod. Initially, foundry-db-update runs before the other foundry pods are deployed. Once the other foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.

    **Volt MX Go Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/)**.

    !!!note
        - If you defined a different Volt MX Go Foundry hostname, the Foundry URL would be the defined Foundry hostname concatenated with `/mfconsole/`.
        - If you want to access this deployment from a remote machine, you most likely need to update the `/etc/hosts` file on the remote machine as well.
        
        - To create an account, see [Create a Volt MX Go Foundry administrator account](../howto/foundryadminaccount.md).
        
        - To connect to Domino server from your Notes client, see [Connect to Domino server from your Notes client](../howto/connectdominofromnotes.md).

6. (Optional) Perform monitoring procedures.

    Perform the procedures under [Monitoring](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Monitoring.html) in the HCL Volt MX documentation.

    !!!note
        The procedures are for enabling important monitoring features such as Metrics Server, Elastic Stack, Kuberhealthy.

7. (Optional) Perform post installation tasks.

    Perform the procedures under the [Post Installation Tasks](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html) in the HCL Volt MX documentation.



### For Volt MX Go v2.0.4 or earlier

!!!note
    Up to Volt MX Go v2.0.4, the following helm charts are used for Volt MX Go Foundry installation:

        - `voltmx-dbupdate`
        - `voltmx-foundry`

1. Create a namespace and a temp directory for the charts.

    Run the following commands to create a namespace, set the current context to **mxgo**, create a temp directory for downloading the charts, and make it the current directory:

    ```
    kubectl create namespace mxgo
    kubectl config set-context --current --namespace=mxgo
    mkdir ~/mxgo
    cd ~/mxgo
    ```

    --8<-- "restartwindows.md"

2. Configure Helm to pull from HCL Container Repository.

    The procedure sets up Helm with the details necessary to authenticate with the HCL Container Repository. You will need your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

    - Run the following command to set up Helm:

        ```
        helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
        ```

        !!!example
            `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`


        !!!note
            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

        If you get an error message similar to the following:

        ``` { .yaml .no-copy }
        Error: looks like https://hclcr.io/chartrepo/voltmxgo is not a valid chart repository or cannot be reached: failed to fetch https://hclcr.io/chartrepo/voltmxgo/index.yaml : 401 Unauthorized
        ```

        Most likely, you haven't specified your username or authentication token correctly. Make sure the case and content matches exactly what's listed on the HCL Container Repository site and retry.

3. Download Foundry charts.

    1. Run the following command to make sure that the chart information for the repositories is up-to-date.

        ```
        helm repo update
        ```

        --8<-- "helmversion.md"

    2. Run the following commands to download the Foundry charts, unpack the files, and move the `values.yaml` file to the current directory:

        ```
        mkdir foundry
        cd foundry
        helm pull hclcr/voltmx-dbupdate
        helm pull hclcr/voltmx-foundry
        tar -xzf voltmx-foundry-1.n.n.tgz
        tar -xzf voltmx-dbupdate-1.n.n.tgz
        mv voltmx-foundry/values.yaml  ./
        mv voltmx-foundry/init-guids.sh  ./
        chmod +x init-guids.sh
        ```
        !!!note
            The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.


    3. Volt MX Go Foundry uses several Global Unique IDs to distinguish different installations of Volt MX Go Foundry. Invoke the init-guids script to generate the IDs using the following command:
        ```
        ./init-guids.sh --new
        ```

    4. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and `your-authentication-token` with your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

        ```{ .yaml .no-copy }
        imageCredentials:
        username: your-email
        password: your-authentication-token
        ```

        !!!note
            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

    5. Locate the following line in the file and add your Volt MX Go Foundry server domain name setting:

        ```{ .yaml .no-copy }
        serverDomainName:
        ```
        
        Whatever server domain name you specify here, you need to ensure that it's resolvable. There is no additional work if you have already registered your server domain name in DNS. However, if you haven't registered it, you must add it to the server's /etc/hosts file [Ensure Foundry Hostnames are resolvable](prereqindex.md#for-first-time-installation-of-volt-mx-go), substituting your server domain name. Additionally, you must make the same updates in k3s's coredns config map as described in [For K3s only](prereqindex.md#for-first-time-installation-of-volt-mx-go) again substituting your server domain name.

    6. Locate the following lines in the file and add your Volt MX Go Foundry database details:

        ```{ .yaml .no-copy }
        ### Database details ###

        # Database type which you want to use for Volt MX Go Foundry (String)
        # Possible values:
        #   "mysql" for MySQL DB server
        #   "sqlserver" for Azure MSSQL or SQLServer
        #   "oracle" for Oracle DB server
        dbType:

        # Database server hostname (String)
        dbHost:

        # Database server port number (Number). This can be empty for cloud managed service.
        dbPort:

        # Database User and password - you may set a single general userid/password here,
        # or you may set specific userid/password combinations below.  If set, the
        # specific values override the general dbUser/dbPass.

        # Database server user (String)
        dbUser:

        # Database server password (String) enclosed in quotes
        dbPass:
        ```

    7. For more advanced configuration options, see [Configuration](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#configuration) in the *Installation Guide for Volt MX Foundry Containers Helm Installation*.

    8. Save the file and exit.

4. (Optional) Perform advanced scenario procedures.

    Perform the procedures under [Advanced Scenarios](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Advanced_Scenarios.html).


5. Deploy Foundry's dbupdate to create the databases.

    1. Run the following Helm install command to deploy Foundry's dbupdate:

        ```
        helm install dbupdate voltmx-dbupdate -f values.yaml
        ```

    2. Run the following command to verify deployment completion of Foundry's dbupdate:

        ```
        kubectl get pods -o wide -w
        ```

        The output should be similar to the following and will update over time:

        ```{ .yaml .no-copy }
        NAME                            READY   STATUS      RESTARTS   AGE
        domino-drapi-6d755b68df-2sfhb   3/3     Running     0          6m13s
        mysql-0                         1/1     Running     0          2m37s
        foundry-db-update-dzdrx         1/1     Running     0          24s
        foundry-db-update-dzdrx         0/1     Completed   0          65s
        foundry-db-update-dzdrx         0/1     Completed   0          67s
        foundry-db-update-dzdrx         0/1     Completed   0          68s
        ```

    3. Once the foundry-db-update pod shows Completed in the STATUS column, the databases have been created. Press `Ctrl-c` to stop the kubectl command.

6. Install Volt MX Go Foundry.

    1. Run the following Helm install command to deploy Volt MX Go Foundry:

        ```
        helm install foundry voltmx-foundry -f values.yaml
        ```

    2. Run the following command to verify when the Volt MX Go Foundry install is ready:

        ```
        kubectl get pods -o wide -w
        ```

        The output should be similar to the following and will update over time:

        ![output](../assets/images/output1.png)


    3. Monitor all the foundry pods except for the foundry-db-update pod as it has already been completed. Once the other foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.

    **Volt MX Go Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/)**.

    !!!note
        - If you defined a different Volt MX Go Foundry hostname, the Foundry URL would be the defined Foundry hostname concatenated with `/mfconsole/`.
        - If you want to access this deployment from a remote machine, you most likely need to update the `/etc/hosts` file on the remote machine as well.
        
        - To create an account, see [Create a Volt MX Go Foundry administrator account](../howto/foundryadminaccount.md).
        
        - To connect to Domino server from your Notes client, see [Connect to Domino server from your Notes client](../howto/connectdominofromnotes.md).


7. (Optional) Perform monitoring procedures.

    Perform the procedures under [Monitoring](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Monitoring.html) in the HCL Volt MX documentation.

    !!!note
        The procedures are for enabling important monitoring features such as Metrics Server, Elastic Stack, Kuberhealthy.

8. (Optional) Perform post installation tasks.

    Perform the procedures under the [Post Installation Tasks](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html) in the HCL Volt MX documentation.

## For single container solution

For more information, see [Volt Foundry Single Container Solution](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html) in the Volt MX Documentation. 

### For Volt MX Go v2.1

#### Before you begin

- You have completed all the [installation prerequisites](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html#prerequisites).
- You have reviewed the configuration parameters and identified their required values as you must provide them during the installation. For more information, see [Configuration](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html#configuration).
- You have downloaded the Volt Foundry Single Container install script. For more information, see [Download HCL Volt MX Go Release package](http://localhost:8000/voltmxgo-documentation/tutorials/portaldownload.html#for-volt-mx-go-v21). 

#### Install Volt Foundry

1. Click the link to the installation guide and follow the installation steps. 

    [Volt Foundry Single Container Solution installation guide](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_single_container/Content/VoltMX_Foundry_Single_Container_Solution_On-Prem_.html#installation)

    !!!warning "Important"
        - The installation guides indicate installation files and installation file download locations. **You must use the installer you downloaded as indicated in the *Before you begin* section.**
        - Make sure to check all the details and complete all the applicable steps indicated in the installation guide.

2. Update the `docker-compose.yml` file.

    1. Locate the `docker-compose.yml` file in the Volt Foundry directory.
    2. Open the `docker-compose.yml` file with your preferred editor and locate the line containing the `image:` key.
    3. Change the value of the `image:` key from `"hclcr.io/voltmx/voltmx-foundry-db:<version>_GA"` to `"hclcr.io/voltmxgo/voltmx-foundry-db:<version>_GA"`, wherein <version\> corresponds to the Volt Foundry release version. For example, `"hclcr.io/voltmxgo/voltmx-foundry-db:9.5.18.0_GA"`.
    4. Save your changes and close the file. 

3. Stop the existing images by running the command `docker compose down`.
4. Restart the images by running the command `docker compose up -d`.


## Next step

After completing the installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install Volt MX Go Iris](installiris.md).

-->