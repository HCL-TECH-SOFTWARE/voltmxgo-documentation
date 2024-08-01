# Upgrade Volt MX Go server components

The following procedures guide you in upgrading the server components of Volt MX Go.

--8<-- "browsertab.md"

## Upgrade Domino REST API

--8<-- "drapiversion.md"

1. Downloaded the required version of the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html#download-the-domino-rest-api) in the HCL Domino REST API documentation.

2. Follow the relevant steps in the [upgrade procedure](https://opensource.hcltechsw.com/Domino-rest-api/howto/production/versionupdate.html) in the HCL Domino REST API documentation based on your installation platform.

## Upgrade Volt MX Go Foundry

As Volt MX Go Foundry supports various installation mechanisms, refer to the relevant upgrade procedure.

### For using an installer

!!!warning "Important"
    The upgrade process works by upgrading the existing database to the latest version, and installing fresh application server artifacts, such as data sources and WARs. For installation details such as hostname, database port, prefix, suffix, you must refer to the installation logs of your previous setup.

    The installer does not support automatic backups of database and other artifacts. You must clean up the existing application server artifacts and take a backup of the custom artifacts.
    The installer also does not support rollback in case of a failure during the upgrade. To roll back, restore the database and server artifacts you backed up before upgrading.

#### Before you begin

- Back up your databases and server artifacts.
- You have downloaded the latest Volt MX Go Foundry installer based on your used installation platform/option. For more information, see [Download HCL Volt MX Go Release package](portaldownload.md).

- Ensure that the installer has execute permission.
- Ensure that you have the path of your previous installation directory.
- Ensure that you stop the application server of your existing Volt MX Go Foundry instance, which you want to upgrade.

#### Procedure

- Follow the link to the upgrade procedure based on your used installation platform/option:

    !!!warning "Important"
        - The upgrade procedure will indicate installation files and installation file download locations. **You must use the installer you downloaded in *Before you begin*.**
        - Check all the details and complete all the applicable steps indicated in the upgrade procedure.

    - [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    
    - [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Upgrading_VoltMX_Foundry_SP1.html)
    <!-- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html)-->

### For using helm charts on a supported Kubernetes platform

#### Before you begin

1. Create a temp directory for the charts.

    Run the following to create a temp directory for downloading the charts, and make it the current directory:

    **Command:**
    ```
    mkdir ~/<new directory name>
    cd ~/<new directory name>
    ```

    **Example:**
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
            The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.


4. Obtain the `upgrade.properties` file from your prior deployment and copy it into the same directory as your `values.yaml`.
5. Invoke the init-guids script specifying the file path of the prior deployment's `upgrade.properties` by running the following command:

    ```
    ./init-guids.sh --upgrade ./
    ```

#### Procedure

--8<-- "verupgrade.md"

## Additional information

After completing the upgrade installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install and upgrade Volt MX Go Iris](installiris.md).

