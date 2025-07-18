# For Volt MX Go v2.0.4 or earlier - EOS

--8<-- "endofsupport.md"

## Install Domino REST API

Guides you in installing Domino REST API.

### Before you begin

--8<-- "drapiversion.md"

### Procedure

1. Download the Domino REST API installer. For more information, see [Download the Domino REST API](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html#download-the-domino-rest-api "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Domino REST API documentation.

2. Follow the links to the installation procedure based on your preferred installation platform:

    - [For Windows](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/win.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

    - [For Linux](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/linux.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

3. Complete all the [post-installation tasks](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/postinstallation.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.

For more information, see the [Installation and configuration](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} page in the [HCL Domino REST API documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.

## Install Volt Foundry

Volt Foundry supports the following installation mechanisms:

- Use the Windows or Linux installers that use Install Anywhere to do the installation. It allows you to install a bundled Tomcat or JBoss app server or install it onto an existing app server (JBOSS single or multi-node, or WebLogic).
- Use the Command Line installer for advanced deployments.
- Use helm charts on one of the supported Kubernetes platforms, including OpenShift, AKS (Azure), EKS (AWS), and GKE (Google).

### For using an installer

#### Before you begin

You have downloaded the latest version of Volt Foundry installer based on your preferred installation platform/option. For more information, see [Download HCL Volt MX Go installers](../portaldownload.md#for-volt-mx-go-v204-and-earlier).

#### Procedure <!--Install Volt Foundry-->

For installing Volt Foundry, click the link to the installation guide corresponding to your installation platform and follow the installation steps.

!!!warning "Important"
    - The installation guides indicate installation files and installation file download locations. **You must use the installer you downloaded as indicated in the *Before you begin* section.**
    - Make sure to check all the details and complete all the applicable procedures indicated in the sections in the installation guides.

- [For Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_windows_install_guide/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For Linux](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_linux_install_guide/Content/Introduction.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

- [For command line installer](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/VoltMX_Foundry_CLI/Content/installer_cli.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}

### For using helm charts on a supported Kubernetes platform

#### Before you begin
  
!!! note "Prerequisite"

    [Obtain authentication token from HCL Container Repository](../../../howto/operation/obtainauthenticationtoken.md) before proceeding.

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

    The procedure sets up Helm with the details necessary to authenticate with the HCL Container Repository. You will need your [email and authentication token](../../../howto/operation/obtainauthenticationtoken.md) used with the HCL Container Repository.

    - Run the following command to set up Helm:

        ```
        helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
        ```

        !!! example

            `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`

        !!! note

            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](../../../howto/operation/obtainauthenticationtoken.md) as your authentication token or password.

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

        See [Volt MX Go and Helm chart version compatibility](../../../references/compatibilitymatrix.md#volt-mx-go-and-helm-chart-version-compatibility) to know the latest Helm chart version.

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


    3. Volt Foundry uses several Global Unique IDs to distinguish different installations of Volt Foundry. Invoke the init-guids script to generate the IDs using the following command:

        ```
        ./init-guids.sh --new
        ```

    4. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and `your-authentication-token` with your [email and authentication token](../../../howto/operation/obtainauthenticationtoken.md) used with the HCL Container Repository.

        ```{ .yaml .no-copy }
        imageCredentials:
        username: your-email
        password: your-authentication-token
        ```

        !!! note

            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](../../../howto/operation/obtainauthenticationtoken.md) as your authentication token or password.

    5. Locate the following line in the file and add your Volt Foundry server domain name setting:

        ```{ .yaml .no-copy }
        serverDomainName:
        ```

        Whatever server domain name you specify here, you need to ensure that it's resolvable. There is no additional work if you have already registered your server domain name in DNS. However, if you haven't registered it, you must add it to the server's `/etc/hosts` file<!--[Ensure Foundry Hostnames are resolvable](prereqindex.md#for-first-time-installation-of-volt-mx-go)-->, substituting your server domain name. Additionally, you must make the same updates in k3s's coredns config map <!--as described in [For K3s only](prereqindex.md#for-first-time-installation-of-volt-mx-go)-->and substituting your server domain name.

    6. Locate the following lines in the file and add your Volt Foundry database details:

        ```{ .yaml .no-copy }
        ### Database details ###

        # Database type which you want to use for Volt Foundry (String)
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

    7. For more advanced configuration options, see [Configuration](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html#configuration "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the *Installation Guide for Volt MX Foundry Containers Helm Installation*.

    8. Save the file and exit.

4. (Optional) Perform advanced scenario procedures.

    Perform the procedures under [Advanced Scenarios](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Advanced_Scenarios.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"}.


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

6. Install Volt Foundry.

    1. Run the following Helm install command to deploy Volt Foundry:

        ```
        helm install foundry voltmx-foundry -f values.yaml
        ```

    2. Run the following command to verify when the Volt Foundry install is ready:

        ```
        kubectl get pods -o wide -w
        ```

        The output should be similar to the following and will update over time:

        ![output](../../../assets/images/output1.png)


    3. Monitor all the foundry pods except for the foundry-db-update pod as it has already been completed. Once the other foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.

    **Volt Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/)**.

    !!! note
        - If you defined a different Volt Foundry hostname, the Foundry URL would be the defined Foundry hostname concatenated with `/mfconsole/`.
        - If you want to access this deployment from a remote machine, you most likely need to update the `/etc/hosts` file on the remote machine as well.

        - To create an account, see [Create a Volt Foundry administrator account](../../../howto/install/foundryadminaccount.md).
        
        - To connect to Domino server from your Notes client, see [Connect to Domino server from your Notes client](../../../howto/install/connectdominofromnotes.md).


7. (Optional) Perform monitoring procedures.

    Perform the procedures under [Monitoring](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_Monitoring.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX documentation.

    !!!note
        The procedures are for enabling important monitoring features such as Metrics Server, Elastic Stack, Kuberhealthy.

8. (Optional) Perform post installation tasks.

    Perform the procedures under the [Post Installation Tasks](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm_PostInstallation.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX documentation.

## Next step

After completing the installation of **Domino REST API** and **Volt Foundry**, proceed to [Install Volt Iris](../installiris/upgradeiris.md).
