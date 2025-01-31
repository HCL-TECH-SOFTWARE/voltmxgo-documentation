# For Volt MX Go v2.0.4 or earlier

Guides you in upgrading Volt MX Go server components.

## Upgrade Domino REST API

### Before you begin

--8<-- "drapiversion.md"

### Procedure

1. Downloaded the required version of the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html#download-the-domino-rest-api) in the HCL Domino REST API documentation.

2. Follow the relevant steps in the [upgrade procedure](https://opensource.hcltechsw.com/Domino-rest-api/howto/production/versionupdate.html) in the [HCL Domino REST API documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html) based on your installation platform.

## Upgrade Volt MX Go Foundry

The following procedures guide you in upgrading Volt MX Go Foundry to the latest version. As Volt MX Go Foundry supports various installation mechanisms, refer to the relevant upgrade procedure.

### For using an installer

!!!warning "Important"
    The upgrade process works by upgrading the existing database to the latest version, and installing fresh application server artifacts, such as data sources and WARs. For installation details such as hostname, database port, prefix, suffix, you must refer to the installation logs of your previous setup.

    The installer does not support automatic backups of database and other artifacts. You must clean up the existing application server artifacts and take a backup of the custom artifacts.
    The installer also does not support rollback in case of a failure during the upgrade. To roll back, restore the database and server artifacts you backed up before upgrading.

#### Before you begin

- Back up your databases and server artifacts.
- You have downloaded the latest Volt MX Go Foundry installer based on your used installation platform/option. For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v204-or-earlier).

- Ensure that the Volt MX Go Foundry installer has execute permission.
- Ensure that you have the path of your previous installation directory.
- Ensure that you stop the application server of your existing Volt MX Go Foundry instance, which you want to upgrade.

#### Procedure

- Follow the link to the upgrade procedure based on your used installation platform:

    !!!warning "Important"
        - The upgrade procedure will indicate installation files and installation file download locations. **You must use the installer you downloaded in *Before you begin*.**
        - Check all the details and complete all the applicable steps indicated in the upgrade procedure.

    - [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    
    - [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    <!-- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html)-->

### For using Helm charts on a supported Kubernetes platform

#### Before you begin

1. Create a temp directory for the charts.

    Run the following to create a temp directory for downloading the charts, and make it the current directory:

    Command:
    ```
    mkdir ~/<new directory name>
    cd ~/<new directory name>
    ```

    Example:
    ```
    mkdir ~/mxgo201
    cd ~/mxgo201
    ```

    In the example, you create a new directory `mxgo201` that will contain the new Helm charts. Creating the new directory allows you to differentiate and compare the Helm charts from different MX Go versions.

2. Configure Helm to pull from HCL Container Repository.

    You need your [email and authentication token](../howto/obtainauthenticationtoken.md) used with the HCL Container Repository.

    1. Run the following command to check if `hclcr` is already defined:

        ```
        helm repo list
        ```

    2. If `hclcr` is already defined, proceed to **Download Foundry charts** step. Otherwise, execute the following step to set up Helm.

        !!!note
            If `hclcr` points to voltmxgo-ea, you should remove it and then proceed to the next step to set up Helm.

    3. Run the following command to set up Helm:

        ```
        helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
        ```

        !!!example
             `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`


        !!!note
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

        !!!note
            The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.    

            <!--Up to Volt MX Go v2.0.4, the Helm charts `voltmx-dbupdate` and `voltmx-foundry` are used for Volt MX Go Foundry installation.-->

4. Obtain the `upgrade.properties` file from your prior deployment and copy it into the same directory as your `values.yaml`.
5. Invoke the init-guids script specifying the path of the prior deployment's `upgrade.properties` by running the following command:

    ```
    ./init-guids.sh --upgrade ./
    ```

#### Procedure

<!--
!!!note
    Up to Volt MX Go v2.0.4, the following Helm charts are used for Volt MX Go Foundry installation:

    - `voltmx-dbupdate`
    - `voltmx-foundry`
-->

--8<-- "verupgrade.md"

## Next step

After completing the upgrade installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install and upgrade Volt MX Go Iris](installirisindex.md).

<!--# Upgrade Volt MX Go Foundry

The following procedures guide you in upgrading Volt MX Go Foundry to the latest version. As Volt MX Go Foundry supports various installation mechanisms, refer to the relevant upgrade procedure.

## For using an installer

!!!warning "Important"
    The upgrade process works by upgrading the existing database to the latest version, and installing fresh application server artifacts, such as data sources and WARs. For installation details such as hostname, database port, prefix, suffix, you must refer to the installation logs of your previous setup.

    The installer does not support automatic backups of database and other artifacts. You must clean up the existing application server artifacts and take a backup of the custom artifacts.
    The installer also does not support rollback in case of a failure during the upgrade. To roll back, restore the database and server artifacts you backed up before upgrading.

### For Volt MX Go v2.1

Upgrades Volt MX Go Foundry from Volt MX Go v2.0.4 to Volt MX Go v2.1.

#### Before you begin

- Back up your databases and server artifacts.

- You have downloaded the Volt Foundry installer based on your installation platform. The minimum required version is v9.5.18.0. For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v21).

- You have installed the Volt MX Go Plugin Installer. For more information, see [Install Volt MX Go Plugin Installer](nativeinstallers.md#2-install-volt-mx-go-plugin-installer).

- Ensure that the Volt Foundry installer has execute permission.
- Ensure that you have the path of your previous installation directory.
- Ensure that you stop the application server of your existing Volt MX Go Foundry instance, which you want to upgrade.

#### 1. Install Volt Foundry

- Follow the link to the upgrade procedure based on your used installation platform. In this step, upgrade your Volt MX Go Foundry v2.0.4 with the required minimum version of Volt Foundry. 

    !!!warning "Important"
        - For Volt MX Go v2.1, only Volt Foundry using a Tomcat non-clustered application server is supported.
        - The upgrade procedure indicates installation files and installation file download locations. **You must use the installer you downloaded in *Before you begin*.**
        - Check all the details and complete all the applicable steps indicated in the upgrade procedure.
        - Make sure to point to the same database you used for your Volt MX Go Foundry v2.0.4 installation to access all the projects you worked on. 

    - [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    
    - [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    <!-- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html)-->

<!--#### 2. Install Volt MX Go plugins

The procedure enables the installation of Volt MX Go plugins to Volt Foundry to enable Volt MX Go features.

!!!warning "Important"
    - For Volt MX Go v2.1, **you can only install Volt MX Go plugins to Volt Foundry that uses a Tomcat non-clustered application server**.

=== "on Linux"

    1. Open Terminal.
    1. Go to the directory where you installed the Volt MX Go Plugin Installer.
    2. Run the Volt MX Go Plugin Installer by entering the following command and press **Enter**

        `./VoltMXGoPluginInstaller`

        The installation tool opens on the Terminal.

    3. Enter **1** to install Volt MX Go plugins and press **Enter**.
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

#### Important consideration

There are regular updates for Volt Foundry. These updates are major release versions, service packs, and fix packs.

**You must reinstall the Volt MX Go plugins every time you update Volt Foundry**.

### For Volt MX Go v2.0.4 or earlier

#### Before you begin

- Back up your databases and server artifacts.
- You have downloaded the latest Volt MX Go Foundry installer based on your used installation platform/option. For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v204-or-earlier).

- Ensure that the Volt MX Go Foundry installer has execute permission.
- Ensure that you have the path of your previous installation directory.
- Ensure that you stop the application server of your existing Volt MX Go Foundry instance, which you want to upgrade.

#### Procedure

- Follow the link to the upgrade procedure based on your used installation platform:

    !!!warning "Important"
        - The upgrade procedure will indicate installation files and installation file download locations. **You must use the installer you downloaded in *Before you begin*.**
        - Check all the details and complete all the applicable steps indicated in the upgrade procedure.

    - [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    
    - [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    <!-- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html)-->

<!--## For using helm charts on a supported Kubernetes platform

### For Volt MX Go v2.1

#### Before you begin

- You have downloaded the Volt Foundry Helm charts. For more information, see [Download HCL Volt MX Go Release package](./portaldownload.md#for-volt-mx-go-v21). 

#### Upgrade Volt Foundry

1. Click the link to the upgrade guide based on your requirement and follow the steps. 

    - [Upgrade Individual Foundry Components](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html#how-to-upgrade-individual-foundry-components)

    - [Upgrade All Foundry Components](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html#how-to-upgrade-all-foundry-components)

    !!!warning "Important"
        Make sure to check all the details and complete all the applicable steps indicated in the installation guide.

2. After completing all applicable steps in the installation guide, update the `values.yaml` file.

    1. Locate the `values.yaml` file in the Volt Foundry directory.
    2. Open the `values.yaml` file with your preferred editor and locate the line containing the `imageRegistry:` key.
    3. Change the value of the `imageRegistry:` key to `hclcr.io/voltmxgo`.
    4. Save your changes and close the file. 

3. Execute the `helm upgrade foundry` command to upgrade the running images to use Volt MX Go. 

<!--
#### Before you begin

1. Create a temp directory for the charts.

    Run the following to create a temp directory for downloading the charts, and make it the current directory:

    Command:
    ```
    mkdir ~/<new directory name>
    cd ~/<new directory name>
    ```

    Example:
    ```
    mkdir ~/mxgo201
    cd ~/mxgo201
    ```

    In the example, you create a new directory `mxgo201` that will contain the new helm charts. Creating the new directory allows you to differentiate and compare the helm charts from different MX Go versions.

2. Configure Helm to pull from HCL Container Repository.

    You will need your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

    1. Run the following command to check if `hclcr` is already defined:

        ```
        helm repo list
        ```

    2. If `hclcr` is already defined, proceed to **Download Foundry charts** step. Otherwise, execute the following step to set up Helm.

        !!!note
            If `hclcr` points to voltmxgo-ea, you should remove it and then proceed to the next step to set up Helm.

    3. Run the following command to set up Helm:

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
        helm pull hclcr/voltmx-foundry
        tar -xzf voltmx-foundry-1.n.n.tgz
        mv voltmx-foundry/values.yaml  ./
        mv voltmx-foundry/init-guids.sh  ./
        chmod +x init-guids.sh
        ```

        !!!note
            - Starting with Volt MX Go v2.1, only the `voltmx-foundry` helm chart is used for Volt MX Go Foundry installation.
            - The chart name has a version string in the filename. The `helm pull` command will pull down the latest version of the chart. Ensure your tar command uses the correct matching file name.

4. Obtain the `upgrade.properties` file from your prior deployment and copy it into the same directory as your `values.yaml`.
5. Invoke the init-guids script specifying the file path of the prior deployment's `upgrade.properties` by running the following command:

    ```
    ./init-guids.sh --upgrade ./
    ```

#### Procedure

!!!note
    Starting with Volt MX Go v2.1, only the `voltmx-foundry` helm chart is used for Volt MX Go Foundry installation.

--8<-- "verupgrade1.md"

-->

<!--### For Volt MX Go v2.0.4 or earlier

#### Before you begin

1. Create a temp directory for the charts.

    Run the following to create a temp directory for downloading the charts, and make it the current directory:

    Command:
    ```
    mkdir ~/<new directory name>
    cd ~/<new directory name>
    ```

    Example:
    ```
    mkdir ~/mxgo201
    cd ~/mxgo201
    ```

    In the example, you create a new directory `mxgo201` that will contain the new helm charts. Creating the new directory allows you to differentiate and compare the helm charts from different MX Go versions.

2. Configure Helm to pull from HCL Container Repository.

    You will need your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

    1. Run the following command to check if `hclcr` is already defined:

        ```
        helm repo list
        ```

    2. If `hclcr` is already defined, proceed to **Download Foundry charts** step. Otherwise, execute the following step to set up Helm.

        !!!note
            If `hclcr` points to voltmxgo-ea, you should remove it and then proceed to the next step to set up Helm.

    3. Run the following command to set up Helm:

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
            -  Up to Volt MX Go v2.0.4, the helm charts `voltmx-dbupdate` and `voltmx-foundry` are used for Volt MX Go Foundry installation.
            - The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.    

4. Obtain the `upgrade.properties` file from your prior deployment and copy it into the same directory as your `values.yaml`.
5. Invoke the init-guids script specifying the file path of the prior deployment's `upgrade.properties` by running the following command:

    ```
    ./init-guids.sh --upgrade ./
    ```

#### Procedure

!!!note
    Up to Volt MX Go v2.0.4, the following helm charts are used for Volt MX Go Foundry installation:

    - `voltmx-dbupdate`
    - `voltmx-foundry`

--8<-- "verupgrade.md"

## Next step

After completing the upgrade installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install and upgrade Volt MX Go Iris](installirisindex.md).
-->
