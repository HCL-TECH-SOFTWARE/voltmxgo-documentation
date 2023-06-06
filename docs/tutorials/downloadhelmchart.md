# Install Domino REST API

The procedure guides you in downloading the Domino REST API Helm chart and deploying Domino REST API.

## 1. Download the Domino REST API Helm chart

1. Run the following command to make sure that the chart information for the repositories is up-to-date.

    ```
    helm repo update
    ```

2. Run the following command to download the chart:

    ```
    helm pull hclcr/drapi
    ```
    The file `drapi-n.n.n.tgz` is downloaded.

3. Run the following commands to unpack the chart and make the DRAPI directory your current directory:

    ```
    tar -xzvf drapi-0.3.2.tgz
    cd drapi
    ```

4. Edit the `values.yaml` file using your preferred editor to update the file with your HCL Container Repository credentials, and the DNS name settings.

    1. Locate the following lines in the file and replace `your-email` and `your-authentication-token` with your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository:

        ```{ .yaml .no-copy }
        imageCredentials:
            username: your-email
            password: your-authentication-token
        ```

    2. Locate the following lines in the file and add your DNS host name settings:

        ```{ .yaml .no-copy }
        ingress:
            drapiDnsName:
            drapiManagementDnsName:
        ```
        Whatever host names you specify here and later in the Foundry install, you need to ensure that the host names are resolvable. There is no additional work if you have already registered the host names in DNS. However, if you haven't registered them, you must add the host names to the server's /etc/hosts file as described in [Add Early Access Preview Host Names](prereq.md#4-add-early-access-preview-host-names), substituting your host names. Additionally, you must make the same updates in k3s's coredns config map as described in [For K3s only](prereq.md#for-k3s-only) again substituting your host names.

        !!!note
            The default names used in previous Early Access releases were `drapi.mymxgo.com` and `drapi-management.mymxgo.com` respectively.

    3. Locate the following lines in the file for the Administrator's first name, last name, and password. You can leave these values as the current default if you desire. However, if you choose to change them, remember the new values and use them when required such as when you [Run First Touch](firsttouch.md#run-first-touch). Note that `dominoAdminFirstName` and `dominoAdminLastName` are combined with a space to separate them to form the **username**.

        ```{ .yaml .no-copy }
        dominoAdminFirstName: "mxgo"
        dominoAdminLastName: "admin"
        dominoAdminPassword: "password"
        ```

        The following fields may be of interest to you as well:

        ```{ .yaml .no-copy }
        dominoServerDomainName: "ocp"
        dominoOrgName: "ocp"
        dominoServerName: "drapi"
        dominoNetworkHostname: ""
        ```

        Consult the [Table of variables](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/installconfig/docker.html#table-of-variables) in *Run Domino REST API with a Docker image* in  [Domino REST API documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html) to determine if you need to update these fields as well. The mapping of `values.yaml` settings to variables is as follows:

        * dominoServerDomainName = SERVERSETUP_SERVER_DOMAINNAME
        * dominoOrgName = SERVERSETUP_ORG_ORGNAME
        * dominoServerName = SERVERSETUP_SERVER_NAME
        * dominoNetworkHostname = SERVERSETUP_NETWORK_HOSTNAME

    4. Save the file and exit.

## 2. Deploy Domino REST API

1. Deploy Domino REST API by running the following Helm install command:

    ```
    helm install domino . -f values.yaml -n mxgo
    ```

    !!!note
        The images must be pulled. It might take awhile, 90 seconds or longer, for the pod to start.

2. Run the following command to wait for the Domino pod to be running and in the ready state:

    ```
    kubectl get pods -o wide -w
    ```

    !!!note
        The `-w` flag tells the kubectl command to wait, and updates the output over time with any changes.

    Eventually you should see 3/3 in the READY column as shown below:

    ```{ .yaml .no-copy }
    NAME                           READY   STATUS              RESTARTS   AGE
    domino-drapi-68596f98fd-bkpdz  0/3     ContainerCreating   0          34s
    domino-drapi-68596f98fd-bkpdz  3/3     Running             0          72s
    ```

3. Once you see the READY column showing 3/3, press `Ctrl-c` to cancel the command.

## Next step

Proceed to [Install MySql for Foundry](installmysqlfoundry.md).