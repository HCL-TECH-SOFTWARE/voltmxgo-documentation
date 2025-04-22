# Install Volt Foundry

--8<-- "devtestenvironment.md"

The procedure guides you in the installation of Volt Foundry.

<!--
The procedures vary depending on the Volt MX Go release version that you are using. 

## For Volt MX Go v2.1

The procedures are applicable for Volt MX Go v2.1 as only the `voltmx-foundry` helm chart is used for Volt Foundry installation. 

### 1. Download Volt Foundry charts

1. Run the following command to make sure that the chart information for the repositories is up-to-date.

    ```
    helm repo update
    ```

    --8<-- "helmversion.md"

2. Run the following command to download the Volt Foundry chart, unpack the files, and move the `values.yaml` file to the current directory:

    ```
    helm pull hclcr/voltmx-foundry
    tar -xzf voltmx-foundry-1.n.n.tgz
    mv voltmx-foundry/values.yaml  ./
    mv voltmx-foundry/init-guids.sh  ./
    chmod +x init-guids.sh
    ```
    !!!note
        The chart name has a version string in the filename. The `helm pull` command will pull down the latest version of the chart. Ensure your tar command uses the correct matching file name, such as `voltmx-foundry-1.2.7.tgz`.


3. Volt Foundry uses several Global Unique IDs to distinguish different installations of Volt Foundry. Invoke the init-guids script to generate the IDs using the following command:
    ```
    ./init-guids.sh --new
    ```

4. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and   `your-authentication-token` with your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

    ```{ .yaml .no-copy }
    imageCredentials:
      username: your-email
      password: your-authentication-token
    ```

    !!!note
        Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

5. Locate the following line in the file and add your Volt Foundry server domain name setting:

    ```{ .yaml .no-copy }
    serverDomainName:
    ```

    Whatever server domain name you specify here, you need to ensure that it's resolvable. There is no additional work if you have already registered your server domain name in DNS. However, if you haven't registered it, you must add it to the server's /etc/hosts file as described in [Ensure Volt Foundry Hostnames are resolvable](prereqindex.md#for-first-time-installation-of-volt-mx-go), substituting your server domain name. Additionally, you must make the same updates in k3s's coredns config map as described in [For K3s only](prereqindex.md#for-first-time-installation-of-volt-mx-go) again substituting your server domain name.

6. Locate the following lines in the file and add your Volt Foundry database details. Use the example values as they match the values used for the MySQL install in the previous section, **Install MySQL for Volt Foundry**.

    ```{ .yaml .no-copy }
    ### Database details ###

    # Database type which you want to use for Volt Foundry (String)
    # Possible values:
    #   "mysql" for MySQL DB server
    #   "sqlserver" for Azure MSSQL or SQLServer
    #   "oracle" for Oracle DB server
    dbType: "mysql"

    # Database server hostname (String)
    dbHost: "mysql"

    # Database server port number (Number). This can be empty for cloud managed service.
    dbPort: 3306

    # Database User and password - you may set a single general userid/password here,
    # or you may set specific userid/password combinations below.  If set, the
    # specific values override the general dbUser/dbPass.

    # Database server user (String)
    dbUser: "root"

    # Database server password (String) enclosed in quotes
    dbPass: "Password123!"
    ```
    
    See [Installing_Containers_With_Helm.html](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html)
    for more details.

7. **(Optional)** If you would like to install the `Engagement` component, you can do so by locating the following line in the file and setting the value to `true`.

    ```{ .yaml .no-copy }
    engagementEnabled: true
    ```

8. Save the file and exit.

### 2. Install Volt Foundry

1. Run the following Helm install command to deploy Volt Foundry:

    ```
    helm install foundry voltmx-foundry -f values.yaml
    ```
    !!! warning "Important"
        The deployment process takes several minutes (more than 5 minutes based on tests). Kindly wait for the process to complete. Once done, you receive a notification that the application has been deployed successfully, including release, build, database, and application information. Otherwise, you will receive an error notification that the deployment is unsuccessful.

2. Run the following command to verify when the Volt Foundry install is ready:

    ```
    kubectl get pods -o wide -w
    ```

    The output should be similar to the following and will update over time:

    ![output](../assets/images/output11.png)


3. Monitor all the foundry pods and the foundry-db-update pod. Initially, foundry-db-update runs before the other foundry pods are deployed. Once the other foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.

**Volt Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/)**.

!!!note
    - If you defined a different Volt Foundry hostname, the Volt Foundry URL would be the defined Volt Foundry hostname concatenated with `/mfconsole/`.
    - If you want to access this deployment from a remote machine, you most likely need to update the `/etc/hosts` file on the remote machine as well. Specify the **IPv4 address** for the Windows system where Volt Foundry is installed. If using a wired connection, use the **IPv4 Address** under **Ethernet adapter Ethernet 3**. If using a wireless connection, use the **IPv4 Address** under **Wireless LAN adapter Wi-Fi**.
    
    
    - To create an account, see [Create a Volt Foundry administrator account](../howto/foundryadminaccount.md).
    
    - To connect to Domino server from your Notes client, see [Connect to Domino server from your Notes client](../howto/connectdominofromnotes.md).

Process to [Next step](#next-step).

## For Volt MX Go v2.0.4 or earlier

The procedures are applicable for Volt MX Go v2.0.4 or earlier versions as the following helm charts are used for Volt Foundry installation:

- `voltmx-dbupdate`
- `voltmx-foundry`

-->

## Download Volt Foundry charts

1. Run the following command to make sure that the chart information for the repositories is up-to-date.

    ```
    helm repo update
    ```

    --8<-- "helmversion.md"

2. Run the following commands to download the Volt Foundry charts, unpack the files, and move the `values.yaml` file to the current directory:

    ```
    helm pull hclcr/voltmx-dbupdate
    helm pull hclcr/voltmx-foundry
    tar -xzf voltmx-foundry-1.n.n.tgz
    tar -xzf voltmx-dbupdate-1.n.n.tgz
    mv voltmx-foundry/values.yaml  ./
    mv voltmx-foundry/init-guids.sh  ./
    chmod +x init-guids.sh
    ```
    !!!note
        The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names, such as `voltmx-foundry-1.2.7.tgz` and `voltmx-dbupdate-1.2.7.tgz`.


3. Volt Foundry uses several Global Unique IDs to distinguish different installations of Volt Foundry. Invoke the init-guids script to generate the IDs using the following command:
    ```
    ./init-guids.sh --new
    ```

4. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and   `your-authentication-token` with your [email and authentication token](../howto/obtainauthenticationtoken.md) used with the HCL Container Repository.

    ```{ .yaml .no-copy }
    imageCredentials:
      username: your-email
      password: your-authentication-token
    ```

    !!!note
        Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](../howto/obtainauthenticationtoken.md) as your authentication token or password.

5. Locate the following line in the file and add your Volt Foundry server domain name setting:

    ```{ .yaml .no-copy }
    serverDomainName:
    ```

    Whatever server domain name you specify here, you need to ensure that it's resolvable. There is no additional work if you have already registered your server domain name in DNS. However, if you haven't registered it, you must add it to the server's /etc/hosts file as described in [Ensure Volt Foundry Hostnames are resolvable](prereqindex.md#for-first-time-installation-of-volt-mx-go), substituting your server domain name. Additionally, you must make the same updates in k3s's coredns config map as described in [For K3s only](prereqindex.md#for-first-time-installation-of-volt-mx-go) again substituting your server domain name.

6. Locate the following lines in the file and add your Volt Foundry database details. Use the example values as they match the values used for the MySQL install in the previous section, **Install MySQL for Volt Foundry**.

    ```{ .yaml .no-copy }
    ### Database details ###

    # Database type which you want to use for Volt Foundry (String)
    # Possible values:
    #   "mysql" for MySQL DB server
    #   "sqlserver" for Azure MSSQL or SQLServer
    #   "oracle" for Oracle DB server
    dbType: "mysql"

    # Database server hostname (String)
    dbHost: "mysql"

    # Database server port number (Number). This can be empty for cloud managed service.
    dbPort: 3306

    # Database User and password - you may set a single general userid/password here,
    # or you may set specific userid/password combinations below.  If set, the
    # specific values override the general dbUser/dbPass.

    # Database server user (String)
    dbUser: "root"

    # Database server password (String) enclosed in quotes
    dbPass: "Password123!"
    ```
    
    See [Installing_Containers_With_Helm.html](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmxfoundry_containers_helm/Content/Installing_Containers_With_Helm.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}
    for more details.

7. **(Optional)** If you would like to install the `Engagement` component, you can do so by locating the following line in the file and setting the value to `true`.

    ```{ .yaml .no-copy }
    engagementEnabled: true
    ```

8. Save the file and exit.

## Deploy Volt Foundry's dbupdate to create the databases in MySql

1. Run the following Helm install command to deploy Volt Foundry's dbupdate:

    ```
    helm install dbupdate voltmx-dbupdate -f values.yaml
    ```

2. Run the following command to verify deployment completion of Volt Foundry's dbupdate:

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

3. Once the foundry-db-update pod shows Completed in the STATUS column, the databases have been created in MySql. Press `Ctrl-c` to stop the kubectl command.

## Install Volt Foundry

1. Run the following Helm install command to deploy Volt Foundry:

    ```
    helm install foundry voltmx-foundry -f values.yaml
    ```

2. Run the following command to verify when the Volt Foundry install is ready:

    ```
    kubectl get pods -o wide -w
    ```

    The output should be similar to the following and will update over time:

    ![output](../assets/images/output1.png)


3. Monitor all the foundry pods except for the foundry-db-update pod as it has already been completed. Once the other foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.

**Volt Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/)**.

!!!note
    - If you defined a different Volt Foundry hostname, the Volt Foundry URL would be the defined Volt Foundry hostname concatenated with `/mfconsole/`.
    - If you want to access this deployment from a remote machine, you most likely need to update the `/etc/hosts` file on the remote machine as well. Specify the **IPv4 address** for the Windows system where Volt Foundry is installed. If using a wired connection, use the **IPv4 Address** under **Ethernet adapter Ethernet 3**. If using a wireless connection, use the **IPv4 Address** under **Wireless LAN adapter Wi-Fi**.
    
    - To create an account, see [Create a Volt Foundry administrator account](../howto/foundryadminaccount.md).
    
    - To connect to Domino server from your Notes client, see [Connect to Domino server from your Notes client](../howto/connectdominofromnotes.md).

## Next step

Proceed to [Install Volt Iris](installirisindex.md).